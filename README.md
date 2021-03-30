# kube-bitwarden_rs
Minikube CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/minikube-deployment.yml/badge.svg?branch=master)

Microk8s CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/microk8s-deployment.yml/badge.svg?branch=master)

## A Kubernetes deployment for bitwarden_rs
These manifests provide a way to deploy fully functional `bitwarden_rs` application, using `nginx-ingress-controller` as ingress controller.

This project is based on https://github.com/icicimov/kubernetes-bitwarden_rs/ repository but it includes modifications for being compatible with Kubernetes >= 1.18 and allows to use an external database instead of sqlite.

## Note: For Kubernetes version between 1.14 to 1.18 please use ingress-backwards.yml which use API networking.k8s.io/v1beta1 and a different syntax
ingress-backwards.yml for k8s between v1.14 to v1.18
ingress.yml for k8s >= 1.19
