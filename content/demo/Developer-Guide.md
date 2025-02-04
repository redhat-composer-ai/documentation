---
title: Demo Developer Guide
draft: false
tags:
  - Demo
  - Developer Guide
---

# Developer Demo Environment

The default [Composer AI Demo Environment](https://catalog.demo.redhat.com/catalog?item=babylon-catalog-prod/sandboxes-gpte.ocp4-composer-ai.prod&utm_source=webapp&utm_medium=share-link) is pointed to the latest stable tag in the [Composer AI Repository](https://github.com/redhat-composer-ai).

## Change Gitops Tag

It may be needed to point to a different tag, branch or even repo when developing content for Composer AI.

### Turning of AutoSync

Because most of Composer runs on App of Apps or the ApplicationSet pattern it can be difficult to turn of autosync. The following instructions will turn off the top level auto sync for most components.

1. Disable auto sync for `Application` `bootstrap` in the main GitOps: `oc patch application bootstrap --type='merge' -p '{"spec": {"template": {"spec": {"syncPolicy": {"automated": {"selfHeal": false}}}}}}' -n openshift-gitops`
2. Disable auto sync for `ApplicationSet` `tenants` on the openshift-gitops namespace: `oc patch applicationset tenants --type='merge' -p '{"spec": {"template": {"spec": {"syncPolicy": {"automated": {"selfHeal": false}}}}}}' -n openshift-gitops`
3. Disable auto sync for `Application` `composer-ai-config` in the Composer AI GitOps: `oc patch application bootstrap --type='merge' -p '{"spec": {"template": {"spec": {"syncPolicy": {"automated": {"selfHeal": false}}}}}}' -n composer-ai-gitops`

At this most of the other Composer AI applications should be modifyable without being controlled by a parent Argo App.

> [!Tip]
> There are a some Application in the Cluster GitOps that may still need extra work in order to prevent auto sync.