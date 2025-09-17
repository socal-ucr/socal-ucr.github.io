---
title: "Setting Up the Workloads"
permalink: /eBPF-tutorial/docs/workload/
excerpt: "Setting up the workloads for tutorial."
last_modified_at: 2024-08-15T08:48:05-04:00
toc: false
---
# Step 5: Setting Up the Workloads(Triton server and client)

In this step, we will set up a Docker container for the Triton server and configure the example model repository.

### 1. Create the Docker Container for the Triton Inference Server

Clone the `server` repository to get the example model repository.

```bash
git clone -b r25.08 https://github.com/triton-inference-server/server.git
cd server/docs/examples
```

### 2. Change the Fetch Model Link

To fetch the models for the server, you'll need to update the fetch model link. You can do this by following the changes suggested in the PR link [here](https://github.com/triton-inference-server/server/pull/7621/files).

After making the necessary changes, run the script to fetch the models:

```bash
./fetch_models.sh
```

### 3. Run Triton Server in Docker

Run the Triton server in a Docker container. Ensure that your model repository path is correctly mapped.

```bash
docker run -it --net=host --pid=host --name=triton-server -v ${PWD}/model_repository:/models nvcr.io/nvidia/tritonserver:24.08-py3 tritonserver --model-repository=/models
```

This will start the Triton server with the models available in the model_repository.

### 4. Verify Triton Server is Running

Once the Triton server starts, it should be up and running, and you should see logs in the terminal indicating that the server has started successfully.

### 5. Setting Up the Triton Inference Client

Pull the Triton Client Docker Image. To install the Triton client, pull the Docker image for the Triton SDK:

```bash
docker pull nvcr.io/nvidia/tritonserver:<xx.yy>-py3-sdk
```
Replace <xx.yy> with the appropriate version tag (e.g., 24.08).

Once these steps are complete, the Triton server should be running, and the Triton client image will be ready for use to interact with the server.
