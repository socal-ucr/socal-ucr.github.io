---
title: "Embedding Access Pattern"
permalink: /eBPF-tutorial/docs/access/
excerpt: "Characterizing Embedding Access Pattern for tutorial dataset."
last_modified_at: 2024-08-15T08:48:05-04:00
toc: false
---

To charaterize the embedding access pattern open `run_dlrm_access_freq.sh`

<figure>
  <img src="{{ '/assets/tutorial/access_pattern.png' }}">
</figure>

Set the `--emb-characterization` to the embedding table number for which you want to characterize the access pattern.

Run the embedding access pattern characterizattion by

```bash
   !./run_dlrm_access_freq.sh
```

You will be able to see the `access_freq.png` under`./input/kaggle` showing the access pattern of given embedding table sorted based on access frequency.

<figure>
  <img src="{{ '/assets/tutorial/access_freq.png' }}">
</figure>

You can observe the skewness in embedding access pattern, and how certain embeddings are accessed way more frequently in comparison to others.
{: .notice--info}

