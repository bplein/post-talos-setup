#MetalLB
Quick installation of MetalLB to give my applications a consistent IP address on my LAN (and from the WAN when applicable)
See https://metallb.io/installation/ for more info

Run their installer:
```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
```

Wait for the pods to come up. Then apply ipaddresspool.yaml, l2advertisement.yaml
```
kubectl -n metallb-system apply -f ipaddresspool.yaml
kubectl -n metallb-system apply -f l2advertisement.yaml
```

I am today only using the first IP address in this pool for all application endpoints.

This IP address needs to be a VALID IP on the "external" network (LAN in my case). MetalLB is going to send requests for URIs coming to it from my firewall to the IP address of the ingress controller, which will map those to the applicatio by URI.