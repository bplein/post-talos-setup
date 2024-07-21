# Ingress-Nginx
Quick installation of ingress-nginx from https://kubernetes.github.io/ingress-nginx/ using the quick deployment documented here https://kubernetes.github.io/ingress-nginx/deploy/

Install via helm chart. I always use the "upgrade --install" syntax because you can run it over and over again with the same CLI
```
helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace --values=values-override.yaml
```

This installs an nginx-ingress controller operating on the first IP in the range used by MetalLB.

Included is [ingress-example.yaml](ingress-example.yaml) that shows creating an ingress for an application that is only supposed to be exposed to a range of IPs representing my local LAN. While this will pick up a publicly resolving IP address, nginx will not let IPs outside this range access the app.