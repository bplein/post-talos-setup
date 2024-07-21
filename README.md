# post-talos-setup

## My home K8s setup

This is my setup for running apps on Talos Linux at home. I have a a fixed IP address and via my pfSense router, I forward all requests coming in on port 80 and 443 to IP address 172.17.0.50 which is the first IP in the range in use by MetalLB. 

![screenshot from pfSense](/images/pfsense.png?raw=true)

I then install Ingress-nginx ingress-controller, and and have it use the loadbalancer, asking for the same IP address. 

I also have cert-manager installed to apply a Let's Encrypt generated cert for each new app. 

Here's a list for you to follow. Feel free to open issues, I might have left some steps out.

[Install MetalLB](01_MetalLB)
[Install ingress-nginx](02_ingress-nginx)
[Install cert-manager](03_cert-manager)