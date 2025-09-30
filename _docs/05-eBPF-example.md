---
title: "eBPF Example Programs"
permalink: /eBPF-tutorial/docs/example/
excerpt: "eBPF Example Codes for kprobes and uprobes"
last_modified_at: 2024-08-15T08:48:05-04:00
toc: false
---

## Basic Hello World Example

The "Hello World" example demonstrates how to use eBPF to trace a specific syscall and print a message. This example attaches to the `execve` syscall, which is responsible for executing programs in Linux.

### Important Steps:

1. **Import the `bcc` library**:
    ```python
    from bcc import BPF
    ```

2. **Define the eBPF program:**
    The program simply prints "Hello World!" when triggered.

    ```python
    program = r"""
    int hello(void *ctx) {
        bpf_trace_printk("Hello World!");
        return 0;
    }
    """
    ```
3. **Attach to the execve syscall:**
    Here, we attach the eBPF program to the `execve` syscall using the BPF library's method to fetch syscall names and attach the probe.

    ```python
    syscall = b.get_syscall_fnname("execve")
    b.attach_kprobe(event=syscall, fn_name="hello")
    ```
4. **Start tracing:**
    The `b.trace_print()` function will print the trace output to the terminal.

    ```python
    b.trace_print()
    ```
    This program will print "Hello World!" to the trace output every time an `execve` syscall is invoked.

## Kprobe Example
In this example, we use eBPF to trace `recvfrom` and `sendto` syscalls in a running Docker container for Triton. It demonstrates how to use kprobes to capture and print information about system calls.

### Important Steps:
1. **Import the necessary libraries:**
    You will need to import the bcc library, as well as Python modules for managing the Docker container and parsing arguments.

    ```python
    from bcc import BPF
    import argparse
    import os
    import ctypes
    ```
2. **Get the container's PID:**
    Use the Docker container name to retrieve the process ID (PID) of the container. This PID is needed to filter the syscalls to the specific Triton process.

    ```python
    def get_pid(container_name):
        cmd = f"docker inspect --format '{{{{.State.Pid}}}}' {container_name}"
        return int(os.popen(cmd).read().strip())
    ```
3. **Create and define the eBPF program:**
    The program tracks the `recvfrom` and `sendto` syscalls. It filters events based on the Triton container's PID and collects information such as the syscall name, file descriptor (fd), and the process name (comm).

    ```python
    bpf_text = """
    int syscall__recvfrom(struct pt_regs *ctx, int fd, void *buf, size_t len, int flags, struct sockaddr *src_addr, __u32 *addrlen) {
        u32 pid = bpf_get_current_pid_tgid() >> 32;
        if (pid != TRITON_PID) return 0;
        // Collect and print data
        return 0;
    }
    """
    ```
4. **Attach the probes:**
    The kprobes are attached to the `recvfrom` and `sendto` syscalls. These probes capture when these syscalls are executed by the Triton process.

    ```python
    b.attach_kprobe(event="__x64_sys_recvfrom", fn_name="syscall__recvfrom")
    b.attach_kprobe(event="__x64_sys_sendto", fn_name="syscall__sendto")
    ```
5. **Read and print events:**
    The `open_ring_buffer` function listens for events and prints the collected data when a syscall is made.

    ```python
    def print_event(cpu, data, size):
        event = ctypes.cast(data, ctypes.POINTER(DataEvent)).contents
        # Print data
    b["events"].open_ring_buffer(print_event)
    ```
6. **Polling the buffer:**
    Finally, the program enters a loop that continuously polls the ring buffer to capture and print data.

    ```python
    b.ring_buffer_poll()
    ```
    This example captures network-related syscalls in the Triton Docker container and prints information like timestamps, PIDs, and the file descriptor used for the syscall.



## Uprobe Example

Uprobes let us trace user-space functions. In this example, we hook into gRPC functions inside the Triton Inference Server binary.

### Important Steps:

1. **Locate the Triton binary inside Docker’s overlay2:**

    ```bash
    docker info | grep "Docker Root Dir"
    # Example: /var/snap/docker/common/var-lib-docker
    ```

    ```bash
    cd /var/snap/docker/common/var-lib-docker/overlay2
    find . -type f -name "tritonserver"
    ```
    
    ```bash
    # Example result:
    /var/snap/docker/common/var-lib-docker/overlay2/6f3e90...dd0f/diff/opt/tritonserver/bin/tritonserver
    ```

2. **Define the eBPF program (filter by container PID):**

    ```python
    // Uprobe: grpc_chttp2_stream constructor
    int trace_constructor(struct pt_regs *ctx) {
        u32 pid = bpf_get_current_pid_tgid() >> 32;
        if (pid != PID) return 0;
        bpf_trace_printk("gRPC Constructor Called - PID: %d\n", pid);
        return 0;
    }
    ```
    ```python
    // Uprobe: grpc_chttp2_maybe_complete_recv_trailing_metadata
    int trace_metadata_func(struct pt_regs *ctx) {
        u32 pid = bpf_get_current_pid_tgid() >> 32;
        if (pid != PID) return 0;
        bpf_trace_printk("gRPC Metadata Function Called - PID: %d\n", pid);
        return 0;
    }
    ```

3. **Attach uprobes to the binary:**

    ```python
    def attach_uprobe_grpc_core(bpf, triton_binary):
        constructor_symbol = "_ZN18grpc_chttp2_streamC1EP21grpc_chttp2_transportP20grpc_stream_refcountPKvPN9grpc_core5ArenaE"
        metadata_symbol   = "_Z49grpc_chttp2_maybe_complete_recv_trailing_metadataP21grpc_chttp2_transportP18grpc_chttp2_stream"

        bpf.attach_uprobe(name=triton_binary, sym=constructor_symbol, fn_name="trace_constructor")
        bpf.attach_uprobe(name=triton_binary, sym=metadata_symbol,   fn_name="trace_metadata_func")
    ```

Run the tracer:

    ```bash
    sudo python triton_uprobes.py \
    --container triton_container_name \
    --binary /var/snap/docker/common/var-lib-docker/overlay2/6f3e90...dd0f/diff/opt/tritonserver/bin/tritonserver
    ```

Example output:

    ```bash
    gRPC Constructor Called - PID: 12345
    gRPC Metadata Function Called - PID: 12345
    ```

This way, the uprobe section only covers the unique parts: finding the binary, the two function probes, and how to run them.

