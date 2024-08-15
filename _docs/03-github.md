---
title: "Setting Up Github Repo"
permalink: /docs/github/
excerpt: "Setting up github repor for tutorial."
last_modified_at: 2024-08-15T08:48:05-04:00
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

Create `input/kaggle` directory for storing input files

```bash
   !mkdir -p input/kaggle
```

Change directory to `input/kaggle`

```bash
   cd input/kaggle
```

Upload the training_dataset `train.npz` file from your mounted Google drive to kaggle directory

<figure>
  <img src="{{ '/assets/tutorial/upload.png' }}">
</figure>

Your Files directory will look like this.

<figure>
  <img src="{{ '/assets/tutorial/directory.png' }}">
</figure>

Change directory to `HPCA_Tutorial`

```bash
   cd ../..
```