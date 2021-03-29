# kube-bitwarden_rs
Minikube CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/minikube-deployment.yml/badge.svg?branch=master)

Microk8s CI/CD status ![bitwarden_rs branch parameter](https://github.com/dark-vex/kube-bitwarden_rs/actions/workflows/microk8s-deployment.yml/badge.svg?branch=master)

## A Kubernetes deployment for bitwarden_rs
These manifests provide a way to deploy fully functional `bitwarden_rs` application, using `nginx-ingress-controller` as ingress controller.
This is based on https://github.com/icicimov/kubernetes-bitwarden_rs/ repo but it includes some modifications for being compatible with Kubernetes >= 1.18 and use an external database instead of sqlite db.

## Adjust the API version in ingress.yml accordling to your kubernetes version
networking.k8s.io/v1beta1 == 1.14 to 1.18
networking.k8s.io/v1 = 1.19+
