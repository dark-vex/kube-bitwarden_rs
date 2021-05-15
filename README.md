# kube-bitwarden_rs
Minikube CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/minikube-deployment.yml/badge.svg?branch=master)

Microk8s CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/microk8s-deployment.yml/badge.svg?branch=master)

## A Kubernetes deployment for bitwarden_rs
These manifests provide a way to deploy fully functional `bitwarden_rs` application, using `nginx-ingress-controller` as ingress controller and `cert-manager` for generate HTTPS certificates.

This project is based on https://github.com/icicimov/kubernetes-bitwarden_rs/ repository but it includes modifications for being compatible with Kubernetes >= 1.18 and allows to use an external database instead of sqlite.

To avoid confusion with the manifests, the project is subdivided in three sections:
```
|kube-bitwarden_rs
├── mysql
├── postgres
├── sqlite
```

## Requirements
- ![cert-manager](https://cert-manager.io/docs/installation/kubernetes/)

- ![nginx-ingress-controller](https://kubernetes.github.io/ingress-nginx/deploy/)


## Installation
Please refer to the specific installation documents for the deployment type you will choose

- ![bitwarden-rs sqlite](https://github.com/dark-vex/kube-bitwarden_rs/blob/master/docs/INSTALL.md)

- ![bitwarden-rs MySQL](https://github.com/dark-vex/kube-bitwarden_rs/blob/master/docs/INSTALL-MySQL.md) (TODO)

- ![bitwarden-rs PostgreSQL](https://github.com/dark-vex/kube-bitwarden_rs/blob/master/docs/INSTALL-PostgreSQL.md) (TODO)


## Note: For Kubernetes version between 1.14 to 1.18 please use ingress-backwards.yml which use API networking.k8s.io/v1beta1 and a different syntax
ingress-backwards.yml for k8s between v1.14 to v1.18

ingress.yml for k8s >= 1.19
