---
layout: splash
permalink: /
title: "  "
hidden: false
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/main.jpg
excerpt: >
  <br />   
---
# Observability into Application-level Metrics with eBPF

To provide greater insight into the complex behavior of modern data centers, non-invasive tools for observability have become increasingly important for data center management and optimization. Observability tools aim to collect various telemetries and measurements of various data center components, such as metrics (bandwidth utilization, memory utilization, etc.), logs, or distributed traces of applications. The emergence of eBPF (extended Berkeley Packet Fil- ter) has revolutionized observability and monitoring tools in the Linux ecosystem. eBPF allows the execution of custom programs in a secure, in-kernel virtual machine, thus providing a unique vantage point for monitoring system-level activities.
Many observability tools have been built with eBPF to provide observability for security, networking activity, container activity, and monitoring of distributed infrastructures, such as Kubernetes. While eBPF has historically be used to provide observability in distributed infrastructures, the use of eBPF to guide management within a single server is not well explored.
This tutorial will introduce the eBPF framework and demonstrate how eBPF can provide observability into data center workloads to guide server management runtimes. The tutorial will include lectures and hands-on demonstrations on the eBPF framework, how to develop eBPF programs for observability, how to interface userspace code with eBPF, and how eBPF-based tools can be used for various server management runtimes, such as resource management and dynamic power management.

## Goal

The goal of this tutorial is to investigate the system bottlenecks associated with placing embedding on CPU main memory and optimizing the embedding placement on commodity servers without scaling the number of GPU devices. We aim to use our work at [VLDB 2022](https://dl.acm.org/doi/10.14778/3485450.3485462).

- Understanding the challenges associated with training big sparse recommendation models on commodity servers using real-world data?
- How to utilize the limited GPU HBM in an efficient way for training big sparse recommendation models.
- Investigate the popularity within training data and how to exploit the skewness in access patterns into embedding tables.
- Traininig big sparse recommendation models on commodity servers with limited GPU devices.

## Audience

Anyone looking for understanding the basics of deep learning based recommendation models and how to train such models.

## Requirements

### Pre-requisites
- Knowledge of basic concepts of deep learning training.
- Familiarity with PyTorch.

### Hardware Resources
- For the tutorial, we will use Google colab so only a Google account is required.


## Schedule

| Time (EST) | Session Details                                           | Speaker                                                | Slides |
| -----------| --------------------------------------------------------- | ------------------------------------------------------ | ------ |
| 8:00 am    | Introduction to Recommender Systems                       | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/) |  [Slides](https://drive.google.com/file/d/15sZ0sDRgi_wcKyNTuc8VaUIU4NXoovYv/view?usp=drive_link)      |
| 8:20 am    | Deep Learning based Recommendation Models (DLRM)          | [Prashant J. Nair](https://prashantnair.bitbucket.io/)      |   [Slides](https://drive.google.com/file/d/1RI4pWZo8oejQMrCBJoPHPsir1F2jodH9/view?usp=sharing)     |
| 8:45 am    | Challenges Associated with Training Recommendation Models | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |   [Slides](https://drive.google.com/file/d/11oEt-CQpKaycQWOaY1f8Z-GO5QYR2loy/view?usp=sharing)     |
| 9:15 am    | Setting Up resources for training                         | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 10:00 am   | Coffee Break                                              |                                                        |        |
| ---------- | --------------------------------------------------------- | ------------------------------------------------------ | ------ |
| 10:20 am   | Skewness in Embedding Access Pattern                      | [Prashant J. Nair](https://prashantnair.bitbucket.io/) |    [Slides](https://drive.google.com/file/d/1XCXuto7UNOfZP61J4-pfhKme0L88UBYB/view?usp=sharing)    |
| 10:40 am   | Baseline DLRM Training Profiling                          | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |   [Slides](https://drive.google.com/file/d/1nO8TZboasRyZMvmx7-0UcQR1Wz8UNcX8/view?usp=sharing)     |
| 11:15 am   | FAE Training                                              | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |   [Slides](https://drive.google.com/file/d/1iPiBZREfml_WaDqQEo1TIstD6FDYImHD/view?usp=sharing)     |
| 12:10 am   | Conclusion                                                | [Prashant J. Nair](https://prashantnair.bitbucket.io/) |        |



{% include feature_row %}
