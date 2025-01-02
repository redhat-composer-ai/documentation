---
title: Infrastructure Overview
draft: false
tags:
  - infra
  - infrastructure
---

# Architecture

The Composer AI Project includes both the code base and a working tech stack for setting up the base generative AI solution, including:

* Composer AI Frontend Application (PatternFly)
* Conductor (Quarkus API Server)
* LLM Serving Runtime (Granite installed on vLLM)
* Vector Database (Elastic)
* Example Ingestion Pipeline (Tekton/KFP)

This allows for developers to be able to quickly deploy the application. Note if you have access to the Red Hat demo platform, there is a pre-provisioned demo that creates a fully functional instance of the application on demand.

## Install Process

* [[Cluster-Infrastructure|Setup Cluster Infrastructure]]
* [[Composer-AI|Install Composer AI Application]]