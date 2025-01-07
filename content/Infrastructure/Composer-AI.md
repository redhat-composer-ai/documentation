---
title: Composer AI Infrastructure
draft: false
tags:
  - infra
---

# Composer AI Infrastructure

## Overview

![[Composer AI Architecture.png]]

The current deployed applications include the following Composer components:

- **Chat UI with Composer Studio** - A PatternFly based web UI designed to allow users to easily create new chat assistants and interact with existing assistants.

- **Conductor Microservice** - A Quarkus based API that hosts the various assistants, which can leverage a RAG pattern with a vector database and various LLMs, and acts as a gateway for any chat application.

- **Document Ingestion Pipeline** - A pipeline that allows users to ingest documents into a vector database using both Tekton and Data Science Pipelines

## Install

### Prerequisite

[[Cluster-Infrastructure|Cluster Setup]] contains all the required infrastructure

> [!Tip]
> If the Cluster GitOps repo was used for cluster setup, then the Composer AI application should be installed by default

### Deploy Components

Installing the components directly can be done from the [App Of Apps Repository](https://github.com/redhat-composer-ai/appOfApps). The install is done through a helm chart located in `appOfApps`, it has been tested deploying through ArgoCD.