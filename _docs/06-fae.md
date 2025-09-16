---
title: "Running FAE"
permalink: /eBPF-tutorial/docs/fae/
excerpt: "Running FAE."
last_modified_at: 2024-08-15T08:48:05-04:00
toc: false
---

To run the FAE with intelligent embedding placement first we need to profile the embeddings based on available GPU memory.
Open `run_fae_profiler.sh`

<figure>
  <img src="{{ '/assets/tutorial/fae_profiling.png' }}">
</figure>

You can change the available GPU memory by `-hot-emb-gpu-mem`

and the sampled inputs for profiling by `--ip-sampling-rate`

Run the fae profiler by 

```bash
   !./run_fae_profiler.sh
```

This step will segregate the training dataset into hot and cold parts with hot embedding dictionary.

<figure>
  <img src="{{ '/assets/tutorial/profiling_stats.png' }}">
</figure>

Observe the percentage of input dataset that only access the hot embeddings.
{: .notice--info}

<figure>
  <img src="{{ '/assets/tutorial/new_dataset.png' }}">
</figure>

Now you can run FAE with segregated data and hot embedding placed on GPU by

```bash
   !./run_dlrm_fae.sh
```

Observe the difference in Hot optimizer time and Cold optimizer time.
{: .notice--info}



