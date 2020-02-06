### Some handcrafted kubernetes deployments

Everything has been done in a bare metal cluster, everything relies on :
* [Metallb](https://github.com/metallb/metallb) for LoadBalancer service type
* [nfs-client-provisioner](https://github.com/kubernetes-incubator/external-storage/tree/master/nfs-client) for PV/PVC
* [nginx-ingress](https://github.com/kubernetes/ingress-nginx) for ingress management
* [cert-manager](https://github.com/jetstack/cert-manager) for Let's Encrypt stuff

If you have brand new and empty Kubernetes cluster, start with them !

Almost everything is made from docker image.

Enjoy !


