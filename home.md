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
# Training Big Sparse Recommendation Models on Commodity Servers

Deep learning based recommendation models are one of the larget DNN workload with several TeraBytes in size and trillions of parameters. Training such big sparse recommendation models on low end GPUs is an open problem. Given the limited capacity of GPU HBM, number of GPU’s scale with embedding table size. Other option is to use commodity servers with limited number of GPU’s where embedding tables are placed on CPU main memory. But placing embedding table on CPU main memory faces system bottlenecks and slows down the overall training process.

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
| 8:00 am    | Introduction to Recommender Systems                       | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/) |  [Slides](https://drive.google.com/file/d/1jzYnnl6GFzDxlHz9p146UzJDlEciciTO/view?usp=sharing)      |
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
