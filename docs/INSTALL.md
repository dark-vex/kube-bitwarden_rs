# Bitwarden_rs sqlite
The application gets deployed as Kubernetes StatefulSet and uses a persistent volume claim for storing our data. Some other settings like CPU and memory resources are set in the statefulset.yml file and can be modified as needed. The app will run as user id 33 (www-data) instead of default root user for increased security. The included RBAC settings in the rbac.yml file provide access only to Kubernetes resources the app needs.


## Settings
The Bitwarden related settings are set in the `configmap.yml` file. 

In case you want to use the email feature, the SMTP password need to be set in the smtp-secret.yml file as base64 encoded values.


### configmap.yml
This file contains mainly the bitwarden settings, if you wish to use the bitwarden email feature you must replace `smtp-*` values and set it accordling to your SMTP service.

A `domain-fqdn` value should be supplied and set also in ingress.yml (see `ingress.yml` section below)
```
  smtp-server: 'smtp.domain.tld'
  smtp-from: 'user@smtp.domain.tld'
  smtp-port: '587'
  smtp-ssl: 'true'
  smtp-username: 'user@smtp.domain.tld'
  domain-fqdn: 'https://bitwarden.domain.tld'
```

### ingress.yml
There is an option to provide TLS certificate for the domain in the ingress.yml via the secretName parameter (Under tls -> hosts) if you haven't done that already in the Nginx proxy settings (this will apply the certificate only to this Ingress only rather than globally for all domains).

In `ingress.yml` file it's necessary to replace the following parameters:
- cert-manager issuer (`cert-manager.io/issuer: letsencrypt-[staging|prod]`) use `letsencrypt-staging` for testing purpose and `letsencrypt-prod` for production

Note: The issuer name (`cert-manager.io/issuer`) shall reflect the naming convention used when creating the Issuer (or ClusterIssuer if used globally), please refer to cert-manager documentation https://cert-manager.io/docs/configuration/acme/

- Under tls -> hosts replace the domain name with the same FQDN used in `configmap.yml`

- Under rules -> host replace the domain name  with the same FQDN used in `configmap.yml`


### smtp-secret.yml
In case you want to use the email feature, the SMTP username and password need to be set in the `smtp-secret.yml` file as `base64` encoded values.

You can quickly replace it with sed

```sh
$ sed -i 's/<BASE64_ENCODED_PASSWORD>/MyPassword/g' ./sqlite/smtp-secret.yml
```

## Install
```sh
$ kubectl create ns bitwarden
$ kubectl apply -f sqlite/ -n bitwarden
```