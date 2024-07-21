#Install cert-manager

First, add the jetstack repo to helm:

`helm repo add jetstack https://charts.jetstack.io --force-update`

Then, install the helm chart:
```
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.15.0 \
  --set crds.enabled=true
```
Finally, add the productuion and staging issuers to the setup.

`kubectl -n cert-manager create -f .`

You should always use the staging issuer until you are satisfied that your app comes up correctly. If there are issues with the app coming up and you are using the production issuer, you could be put on "time out" for hitting the production issuer too often. 