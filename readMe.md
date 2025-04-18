# Palmr Helm Chart

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/KG-khangelani/palmr-helm)](https://artifacthub.io/packages/search?repo=palmr-helm)

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
   ```

2. **Customize the Values**

   Edit the `values.yaml` file to configure PostgreSQL, MinIO (or local storage), and Palmr according to your needs.

3. **Install the Chart**

   ```bash
   helm install my-palmr ./palmr-helm-chart
   ```

   To override settings at install time, use the `--set` flag. For example, to disable MinIO and use local storage:

   ```bash
   helm install my-palmr ./palmr-helm-chart --set minio.enabled=false --set palmr.storage.useMinio=false
   ```

## Configuration

Refer to the `values.yaml` file for a complete list of configurable parameters:

- **PostgreSQL:**
    - `postgres.username`
    - `postgres.password`
    - `postgres.db`
    - `postgres.persistence.size`

- **MinIO:** (enable or disable MinIO deployment)
    - `minio.enabled`
    - `minio.rootUser`
    - `minio.rootPassword`
    - `minio.persistence.size`

- **Palmr:**
    - `palmr.image`
    - `palmr.replicaCount`
    - `palmr.storage.useMinio`  
      Set this to `true` to use MinIO or `false` to use local storage via a dedicated PVC.
    - `palmr.storage.pvc.size`
    - `palmr.storage.pvc.storageClassName`

## Listing on Artifact Hub

To list this Helm chart on Artifact Hub, follow these steps:

1. **Create an Artifact Hub account**: If you don't have one already, create an account on [Artifact Hub](https://artifacthub.io/).

2. **Add a new repository**: Go to your profile and add a new repository. Provide the necessary details such as the repository name, URL, and description.

3. **Upload the `artifacthub-repo.yml` file**: Ensure that the `artifacthub-repo.yml` file is present in the root of your repository. This file contains metadata required by Artifact Hub.

4. **Verify the repository**: Follow the instructions on Artifact Hub to verify your repository. This may involve adding a verification file or DNS record.

5. **Publish the chart**: Once the repository is verified, you can publish your Helm chart on Artifact Hub. This will make it available for others to discover and use.

## Adding the Repository to Artifact Hub

To add this repository to Artifact Hub, follow these steps:

1. **Go to Artifact Hub**: Visit [Artifact Hub](https://artifacthub.io/).

2. **Search for the repository**: Use the search bar to find the `palmr-helm` repository.

3. **Add the repository**: Click on the repository and follow the instructions to add it to your list of repositories.

## Triggering the GitHub Actions Workflow

To automate the deployment process, a GitHub Actions workflow has been added to this repository. Follow these steps to trigger the workflow:

1. **Customize the `values.yaml` file**

   Before triggering the workflow, make sure to customize the `values.yaml` file according to your requirements. This file contains configurable parameters for PostgreSQL, MinIO, and Palmr.

2. **Push changes to the `main` branch**

   The GitHub Actions workflow is triggered by a push to the `main` branch. Make sure your changes are committed and push them to the `main` branch:

   ```bash
   git add .
   git commit -m "Update values.yaml"
   git push origin main
   ```

3. **Monitor the workflow**

   Once the changes are pushed, the GitHub Actions workflow will be triggered automatically. You can monitor the progress of the workflow by navigating to the "Actions" tab in your GitHub repository.

## Credits and Acknowledgements

This Helm chart is intended to simplify the deployment of [Palmr](https://github.com/kyantech/Palmr/tree/main) on Kubernetes.

- **Original Palmr Software:**  
  Developed and maintained by the team at [Kyantech](https://github.com/kyantech/Palmr).  
  For the original Palmr source code and documentation, please visit:
    - GitHub: [https://github.com/kyantech/Palmr/tree/main](https://github.com/kyantech/Palmr/tree/main)
    - Documentation: [https://palmr-docs.kyantech.com.br/](https://palmr-docs.kyantech.com.br/)

This chart was inspired by and builds upon the official Docker Compose configuration files and deployment scripts provided by the Palmr project.

## License

This Helm chart is distributed under the same license as Palmr (BSD-2-Clause). Please review the original project’s repository for full licensing details.

## Support

For support with this Helm chart, please open an issue in this repository. For support with Palmr itself, please refer to the [official documentation](https://palmr-docs.kyantech.com.br/) and [GitHub repository](https://github.com/kyantech/Palmr/tree/main).

---

Happy deploying!
