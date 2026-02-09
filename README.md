# Terraform GCP Docker Image

A lightweight Docker image for running Terraform with Google Cloud Platform (GCP) support, based on Alpine Linux.

## Features

- **Alpine Linux 3.17** - Minimal base image
- **Terraform 1.9.8** - Infrastructure as Code tool
- **Google Cloud SDK 509.0.0** - GCP command-line tools
- **Multi-architecture support** - AMD64 and ARM64 builds
- **Python 3** with pip and crcmod for GCP operations

## Quick Start

### Pull from Docker Hub

```shell
docker pull brighterly/terraform-gcp:terraform-gcp
```

### Build Locally

```shell
cd terraform-gcp
docker build -t brighterly/terraform-gcp .
```

### Run Interactive Shell

```shell
docker run -it brighterly/terraform-gcp bash
```

## Available Tools

- `terraform` - Terraform CLI
- `gcloud` - Google Cloud SDK CLI
- `bash` - Shell
- `python3` - Python 3 with pip
- `curl`, `unzip` - Utility tools

## CI/CD

The project uses GitLab CI/CD to automatically build and publish multi-architecture images:

- **Platforms**: linux/amd64, linux/arm64
- **Trigger**: Changes to `terraform-gcp/` directory on `main` branch
- **Registry**: Docker Hub (`brighterly/terraform-gcp`)

### Available Tags

- `terraform-gcp` - Multi-architecture manifest (recommended)
- `alpine-amd64` - AMD64 specific build
- `alpine-arm64` - ARM64 specific build


