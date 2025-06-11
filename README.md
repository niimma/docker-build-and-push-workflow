# Docker Build and Push Workflow

A reusable GitHub Actions workflow to **build**, **tag**, and **push** Docker images to any OCI-compatible registry.

## Features

- Build args support  
- Multi-arch builds via Buildx  
- Tags with SHA and semantic version  
- Pushes to Docker Hub, GitHub Container Registry (GHCR), or any OCI registry  

## Usage

In your consuming repo, add a workflow that calls this:

```yaml
name: Build & Push Image

on:
  push:
    branches: [ main ]

jobs:
  build:
    uses: niimma/docker-build-and-push-workflow/.github/workflows/build-and-push.yml@v1.0.0
    with:
      registry: ghcr.io
      username: niimma
      image_name: my-app
      tags: latest,${{ github.sha }}
    secrets:
      REGISTRY_TOKEN: ${{ secrets.GHCR_TOKEN }}
