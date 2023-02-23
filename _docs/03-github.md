---
title: "Setting Up Github Repo"
permalink: /docs/github/
excerpt: "Setting up github repor for tutorial."
last_modified_at: 2023-02-23T08:48:05-04:00
toc: false
---

Clone the github repor in your colab using

```bash
   !git clone https://github.com/STAR-Laboratory/Accelerating-RecSys-Training.git
```

Change directory to `HPCA_Tutorial`

```bash
   cd Accelerating-RecSys-Training/HPCA_Tutorial/
```

Create `input` directory for storing input files

```bash
   mkdir input
```

Change directory to `input`

```bash
   cd input/
```

Create `kaggle` directory for Criteo Kaggle dataset

```bash
   mkdir kaggle
```

Change directory to `kaggle`

```bash
   cd kaggle/
```

Copy the training_dataset `train.npz` file from your mounted Google drive to kaggle directory

```bash
   cp ../../../../drive/MyDrive/HPCA_2023_Tutorial/Dataset/train.npz .
```

Your Files directory will look like this.

<figure>
  <img src="{{ '/assets/tutorial/repo_set.png' }}">
</figure>

Change directory to `HPCA_Tutorial`

```bash
   cd ../..
```