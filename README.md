### Some handcrafted kubernetes deployments

Everything has been done in a bare metal cluster, everything relies on :
* [Metallb](https://github.com/metallb/metallb) for LoadBalancer service type
* [nfs-client-provisioner](https://github.com/kubernetes-incubator/external-storage/tree/master/nfs-client) for PV/PVC
* [nginx-ingress](https://github.com/kubernetes/ingress-nginx) for ingress management
* [cert-manager](https://github.com/jetstack/cert-manager) for Let's Encrypt stuff

If you have a brand new and empty Kubernetes cluster, start with them !

Almost everything is made from docker image :
* TS3 contains everything needed to setup a Teamspeak 3 server inside Kubernetes : nobody asked for it but here it is anyway !
* Grav is the well known flat file CMS. It's based on the awesome itherz docker image, all credit does to him.
* Mailu is just a tweak of the official Kubernetes configuration to make it lighter.

Enjoy !


