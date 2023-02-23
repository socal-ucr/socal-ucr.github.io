---
title: "Embedding Access Pattern"
permalink: /docs/access/
excerpt: "Characterizing Embedding Access Pattern for tutorial dataset."
last_modified_at: 2023-02-23T08:48:05-04:00
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

You will be able to see the `access_freq.png` showing the access pattern of given embedding table sorted based on access frequency.

<figure>
  <img src="{{ '/assets/tutorial/access_freq.png' }}">
</figure>

