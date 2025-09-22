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




TODO
- uprobe and how to run
