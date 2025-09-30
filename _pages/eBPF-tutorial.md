---
layout: splash
permalink: /eBPF-tutorial/
title: ""
excerpt: >
  <br /> 
hidden: false
header:
  overlay_color: "#fafbffff"
  overlay_image: "/assets/images/EBPF_logo.png"
  image: "/assets/images/EBPF_logo.png"
---
#### IISWC Tutorial 2025(October 12, 2025)
# Observability into Application-level Metrics with eBPFs

To provide greater insight into the complex behavior of modern data centers, non-invasive tools for observability have become increasingly important for data center management and optimization. Observability tools aim to collect various telemetry and measurements of various data center components, such as metrics (bandwidth utilization, memory utilization, etc.), logs, or distributed traces of applications. The emergence of eBPF (extended Berkeley Packet Filter) has revolutionized observability and monitoring tools in the Linux ecosystem. eBPF allows the execution of custom programs in a secure, in-kernel virtual machine, thus providing a unique vantage point for monitoring system-level activities.

Many observability tools have been built with eBPF to provide observability for security, networking activity, container activity, and monitoring of distributed infrastructures, such as Kubernetes. While eBPF has historically been used to provide observability in distributed infrastructures, the use of eBPF to guide management within a single server is not well explored.

## Goal

This tutorial will introduce the eBPF framework and demonstrate how eBPF can provide observability into data center workloads to guide server management runtimes. The tutorial will include lectures and hands-on demonstrations on the eBPF framework, how to develop eBPF programs for observability, how to interface userspace code with eBPF, and how eBPF-based tools can be used for various server management runtimes.

## Audience

This tutorial is intended for engineers and researchers with a background in systems programming and a general understanding of Linux and networking. No prior experience with eBPF is required.

## Requirements

### Pre-requisites
- Familiarity with Linux and the command line.
- Basic understanding of how servers and data centers operate.
- Familiarity with tools like `ssh`, `git`, and general system administration tasks.

### Hardware Resources
- A laptop with at least 4GB of RAM and 10GB of available disk space.
- A working Linux environment (native or using WSL2 on Windows).
- Preferably, administrative privileges (root/sudo) to install required packages and access kernel-level features.

## Schedule

| Time (PST) | Session Details                                           | Speaker                                                | Slides |
| -----------| --------------------------------------------------------- | ------------------------------------------------------ | ------ |
| 9:00 am    | Welcome Statement                       | [Daniel Wong](https://www.danielwong.org/) |       |
| 9:10 am    | Introduction to eBPF                       | [Mohammadreza Rezvani](https://www.linkedin.com/in/mohammadrezarezvani/) |  TBD      |
| 9:30 am    | Setting up the environment          | [Mohammadreza Rezvani](https://www.linkedin.com/in/mohammadrezarezvani/)      |   TBD     |
| 9:50 am    | eBPF "Hello World" | [Mohammadreza Rezvani](https://www.linkedin.com/in/mohammadrezarezvani/)      |   TBD     |
| 10:20 am   | Coffee Break                                              |                                                        |        |
| 10:40 am   | Introduction to Server-Client Workloads                      | [Muntaka Ibnath](https://ibnathism.github.io/) |    TBD    |
| 11:00 am   | Tracing syscalls using kprobes                          | [Muntaka Ibnath](https://ibnathism.github.io/)      |   TBD     |
| 11:30 am   | Tracing user-space functions using uprobes              | [Muntaka Ibnath](https://ibnathism.github.io/)      |   TBD     |
| 11:50 am   | Closing Statement                                               |[Daniel Wong](https://www.danielwong.org/) |        |

{% include feature_row %}
