---
title: Openshift Cluster Infrastructure
draft: false
tags:
  - infra
  - openshift
  - cluster
  - infrastructure
---

# Openshift Cluster Infrastructure

> [!Note]
> Currently most of our testing is done using an Openshift ROSA Cluster. Minor adjustments may be required if using another cluster.

# Quickstart Guide

The easiest way to install Composer on a new cluster is using the bootstrap script in the [Cluster Gitops](https://github.com/redhat-composer-ai/cluster-gitops) repository. This script automates the following:

- Installs all required operators
- Provisions GPU nodes
- Deploys the Composer application

For detailed information, refer to the repository's README.

## Required Operators

If you are using an existing cluster or performing a custom installation, ensure the following operators are installed:

- OpenShift AI
- OpenShift Service Mesh
- OpenShift Serverless
- Authorino
- NVIDIA GPU Operator
- Node Feature Discovery
- OpenShift GitOps
- OpenShift Pipelines
- Elasticsearch (or another supported vector database)

> [!Note]
> Elasticsearch is the default vector database for demonstration purposes.

When using the bootstrap script, these operators are automatically installed in the `openshift-gitops` namespace by the OpenShift GitOps operator.

## Default Composer Installation

The bootstrap script also creates two namespaces:

- `composer-ai-gitops`: Hosts an Argo CD instance that manages the Composer application.
- `composer-ai-apps`: The namespace where the Composer application resides.

The Argo CD instance deploys Composer using the Helm chart located in the [App of Apps](https://github.com/redhat-composer-ai/appOfApps) repository.

For custom installations on existing clusters, it is recommended to install this Helm chart using GitOps for streamlined management. Refer to the [Composer AI Infrastructure documentation](https://www.google.com/url?sa=E&source=gmail&q=link-to-your-composer-ai-infrastructure-docs) for detailed instructions.