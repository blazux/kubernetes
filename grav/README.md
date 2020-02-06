### Grav deployment for Kubernetes

It's based on the awesone [itherz image](https://hub.docker.com/r/itherz/grav)

One problem with it is that most of the file needed are embedded inside the image file system so :
 * deployment will initiate a container who will copy all file needed on the pv (this can be very very long)
 * then start the real container which will bind the pv in the right folder with all needed files

This is just used on the first launch to get everything required on the volume, then you can edit the deployment to remove the initContainer part.
This will avoid running the init again in case the pods gets restarted/moved.

* Replace "site-grav" with the name you want for your deployment
* Change the domain name in the Ingress part
* Adapt the cert-manager part (change the cluster issuer name, or make it a non-cluster issuer, depending on your config)


Enjoy ! 
