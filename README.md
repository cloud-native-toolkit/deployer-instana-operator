# Techzone Instana Operator pipeline

This repository contains a set of Tekton pipelines to deploy Instana in an IBM Technology Zone `deployer` cluster.

## Prerequisites

An IBM Technology Zone `deployer` cluster is assumed to be configured with an appropriate Red Hat OpenShift version for the solution you wish to deploy, with appropriate sizing.

A `deployer` cluster is configured with the following items:

- ExternalSecrets operator deployed with a ClusterSecretStore configured. The remote ExternalSecrets secret store must include an IBM Entitlement Key.
- Techzone Deployer Tekton tasks deployed ([deploy YAML](https://github.com/cloud-native-toolkit/deployer-tekton-tasks/blob/main/argocd.yaml)).
- OpenShift GitOps configured with [One Touch Provisioning ArgoCD instance](https://github.com/one-touch-provisioning/otp-gitops), and any relevant RBAC rules.
- OpenShift Pipelines operator deployed.
- ConfigMap named pipeline-output in the "default" namespace
- OpenShift Data Foundation

There is also the option to use your own IBM Entitlement key passed in as the parameter ibm-entitlement-key

## Deployment Scripts

`oc apply -f instana-operator-pipeline.yaml` to install the pipeline.

`oc create -f instana-operator-pipeline-run.yaml` to kick off pipeline.
