---
permalink: /about/
title: "About"
excerpt: "Details of tutorial"

last_modified_at: 2023-02-08T11:59:26-04:00
toc: true
---

Recommendation models are an important class of Machine Learning (ML) algorithms that offer a targeted user experience for a variety of web-services. E-commerce websites use recommendation algorithms to suggest purchases, search engines to rank search results, video streaming services to recommend videos, and social networks to suggest relevant posts. Over time, recommendation models have evolved from simple collaborative filtering designs to deep learning based approaches. Deep-learning-based recommendation models are at the core of a wide variety of services and consume significant infrastructure capacity and compute cycles in datacenters. Meta reports that more than 50% of their training cycles and around 80% of inference cycles are devoted to deep learning based recommendation models. Similar trends can be found at Google, Alibaba, and Amazon.

Deep learning based recommendation models are a disaggregated conflation of compute-intensive neural networks, memory-intensive embedding tables, and communication collectives-heavy feature interactions. The embedding tables store the user and item features, and their size is expected to increase as more users and items interact. Production-scale recommendation models are already several TeraBytes in size with trillions of parameters. Size of each components differs based on the use case. This results into model-level heterogeneity across deep-learning based recommendation models. Given the limited capacity of GPU HBM, number of GPU’s scale with embedding table size. Other option is to use commodity servers with limited number of GPU’s where embedding tables are placed on CPU main memory. But placing embedding table on CPU main memory faces system bottlenecks and slows down the overall training process.

The goal of the tutorial is to investigate the system bottlenecks associated with placing embedding on CPU main memory and optimizing the embedding placement on commodity servers without scaling the number of GPU devices. We aim to use our work at [VLDB 2022](https://dl.acm.org/doi/10.14778/3485450.3485462).


## Goal

- Understanding the challenges associated with training big sparse recommendation models on commodity servers using real-world data?
- How to utilize the limited GPU HBM in an efficient way for training big sparse recommendation models.
- Investigate the popularity within training data and how to exploit the skewness in access patterns into embedding tables.
- Traininig big sparse recommendation models on commodity servers with limited GPU devices.



## Schedule

| Time (EST) | Session Details                                           | Speaker                                                | Slides |
| -----------| --------------------------------------------------------- | ------------------------------------------------------ | ------ |
| 8:00 am    | Introduction to Recommender Systems                       | [Prashant J. Nair](https://prashantnair.bitbucket.io/) |        |
| 8:20 am    | Deep Learning based Recommendation Models (DLRM)          | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 8:45 am    | Challenges Associated with Training Recommendation Models | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 9:15 am    | Setting Up resources for training                         | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 10:00 am   | Coffee Break                                              |                                                        |        |
| ---------- | --------------------------------------------------------- | ------------------------------------------------------ | ------ |
| 10:20 am   | Compute vs Memory Intensity                               | [Prashant J. Nair](https://prashantnair.bitbucket.io/) |        |
| 10:40 am   | Baseline DLRM Training Profiling                          | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 11:15 am   | FAE Training                                              | [Muhammad Adnan](http://people.ece.ubc.ca/adnan/)      |        |
| 12:10 am   | Conclusion                                                | [Prashant J. Nair](https://prashantnair.bitbucket.io/) |        |

