# Introduction

Various tasks, implemented as Gradle tasks, to automate setup and configuration of K8s and other tooling to support local development

> These scripts have been verified on macOS Monterey 

# Prerequisites

## Colima Container Runtime

[Colima Installation](https://github.com/abiosoft/colima)

## Kubectl

[Kubectl](https://kubernetes.io/docs/tasks/tools/)

## Minikube

[Minikube](https://minikube.sigs.k8s.io/docs/start/)

## Helm

[Helm 3](https://helm.sh/docs/intro/install/)

# Default Properties

For all tasks please check default values/properties in `gradle.properties`

* GRAFANA_HOST_PORT - Port on the host machine to run grafana on
* K8S_VERSION - Version of K8s deployed to Minikube
* MINIKUBE_CONTAINER_RUNTIME - Container runtime for Minikube, [see](https://minikube.sigs.k8s.io/docs/handbook/config/#runtime-configuration) for valid values. 
* MINIKUBE_CPUS - Number of CPUs allocated to Minikube
* MINIKUBE_MEM - Megabytes of memory to allocate to Minikube
* MONITORING_NAMESPACE - Namespace the monitoring tools are deployed to
* PROM_HELM_CHART - Prometheus and related tools helm chart
* PROM_HELM_RELEASE_NAME - Helm release name for the prometheus stack
* VM_CPUS - Number of CPUS allocated to Colima
* VM_MEM_GIGS - Gigabytes of memory allocated to Colima

# Tasks

## deployK8sCluster

Deploys minikube to the container runtime

### Parameters/Properties

* K8S_VERSION
* MINIKUBE_CONTAINER_RUNTIME
* MINIKUBE_CPUS
* MINIKUBE_MEM

## installMonitoringTools

Deploys Prometheus, Grafana, and Alertmanager to the cluster

### Parameters/Properties

* MONITORING_NAMESPACE
* PROM_HELM_CHART
* PROM_HELM_RELEASE_NAME

## portForwardGrafana

Forward the grafana container port to the host machine port

### Parameters/Properties

* GRAFANA_HOST_PORT
* MONITORING_NAMESPACE
* PROM_HELM_RELEASE_NAME

## startColima

Starts the container runtime

### Parameters/Properties

* VM_CPUS
* VM_MEM_GIGS

## uninstallMonitoringTools

Remove the Prometheus stack and supporting tools from the cluster

### Parameters/Properties

* MONITORING_NAMESPACE
* PROM_HELM_RELEASE_NAME

