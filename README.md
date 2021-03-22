# kube-bitwarden_rs
## A Kubernetes deployment for bitwarden_rs
These manifests provide a way to deploy fully functional `bitwarden_rs` application, using `nginx-ingress-controller` as ingress controller.
This is based on https://github.com/icicimov/kubernetes-bitwarden_rs/ repo but it includes some modifications for being compatible with Kubernetes >= 1.18 and use an external database instead of sqlite db.