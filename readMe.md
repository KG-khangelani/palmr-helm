# Palmr Helm Chart

This Helm chart is designed to deploy [Palmr](https://github.com/kyantech/Palmr/tree/main), an open-source file-sharing platform focused on privacy and security, on your Kubernetes cluster.

Palmr gives you the ability to host your own file transfer service without relying on third-party providers, ensuring full control over your data. For more details about Palmr, please visit the [official documentation](https://palmr-docs.kyantech.com.br/).

## Overview

This chart deploys the following components:

- **PostgreSQL:** Stores metadata and user data.
- **MinIO (Optional):** Provides S3-compatible object storage for file storage.  
  Alternatively, you can choose to use local persistent storage (e.g., backed by Longhorn) if you disable the MinIO deployment.
- **Palmr:** The main application server.

The configuration is adaptable, enabling you to choose the preferred storage backend by simply toggling values in the chart's `values.yaml`.

## Prerequisites

- A Kubernetes cluster (v1.18 or later is recommended).
- Helm 3 or later installed.
- (Optional) A storage class such as Longhorn if you plan to use local persistent storage instead of MinIO.

## Installation

1. **Clone the Chart Repository**

   ```bash
   git clone https://github.com/your-helm-repo/palmr-helm-chart.git
   cd palmr-helm-chart
