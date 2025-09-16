---
title: "Installing eBPF"
permalink: /eBPF-tutorial/docs/install/
excerpt: "Installing eBPF for tutorial."
last_modified_at: 2024-08-15T08:48:05-04:00
toc: false
---
# Step 1: Install Required Dependencies

eBPF tools require some essential packages like clang, llvm, bpfcc-tools, and bpftool. Run the following command to install these packages:

For Ubuntu/Debian-based systems:
sudo apt update
sudo apt install clang llvm libbpfcc-dev linux-headers-$(uname -r) bpfcc-tools iproute2

For CentOS/RHEL-based systems:
sudo yum install clang llvm kernel-devel bpfcc-tools iproute


These tools allow you to compile, inspect, and manage eBPF programs.

Step 2: Install bpftool

bpftool is a utility that helps you manage and inspect eBPF programs. Install it by running the following commands:

For Ubuntu/Debian-based systems:
sudo apt install bpftool

For CentOS/RHEL-based systems:
sudo yum install bpftool


If you face issues with installing bpftool via your package manager (especially for custom or cloud kernels), you can manually compile it from source. Follow the instructions in the bpftool GitHub repository
 to clone and build it manually.

Step 3: Verify bpftool Installation

Once bpftool is installed, verify the installation by checking its version:

bpftool version


You should see an output similar to:

bpftool v5.4


If you see this message, bpftool is correctly installed and ready to use.

Step 4: Install bpftrace (Optional)

For advanced tracing of kernel events using eBPF, you can install bpftrace. This high-level tracing tool makes it easy to attach eBPF programs to tracepoints, function calls, and more.

For Ubuntu/Debian-based systems:
sudo apt install bpfcc-tools bpftrace

For CentOS/RHEL-based systems:
sudo yum install bpfcc-tools bpftrace


Once installed, you can use bpftrace to run dynamic tracing scripts. For example, to trace execve system calls, run:

sudo bpftrace -e 'tracepoint:syscalls:sys_enter_execve { printf("execve syscall: %s\n", comm); }'


This will print the name of the program being executed each time the execve system call is made.

Open colab using [link](https://colab.research.google.com/notebooks/welcome.ipynb#scrollTo=Nma_JWh-W-IF)

Create new notebook.

<figure>
  <img src="{{ '/assets/tutorial/colab_notebook.png' }}">
</figure>

Rename the notbook to `Training_rec.ipynb`

Change the Runtime by `Runtime` --> `Change runtime type`

<figure>
  <img src="{{ '/assets/tutorial/change_runtime.png' }}">
</figure>

Select `python 3` as Runtime type and `T4 GPU` as Hardware accelerator.

<figure>
  <img src="{{ '/assets/tutorial/GPU.png' }}">
</figure>

Connect to your GPU runtime by clicling on `Connect`

You can view your resources by `Connect` --> `View resources`

<figure>
  <img src="{{ '/assets/tutorial/connect.png' }}">
</figure>

You will see a GPU device in resources.

<figure>
  <img src="{{ '/assets/tutorial/resources.png' }}">
</figure>