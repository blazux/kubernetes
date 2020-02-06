### A lighter version of Mailu

Everything in here is based on the Kubernetes deployments files provided directly by [Mailu](https://mailu.io/master/kubernetes/mailu/index.html), all credit goes to them !

Any production deployment should be done according to the official Mailu configuration. This one is for testing purpose, no joke.

Here is the list of modification :
 * Daemosets have been turned into regular single pod deployments
 * 2nd nginx ingress controller (the one provided in the mailu repo) in no more needed
 * front service is now a LoadBalancer one
 * Resources requirements have been removed

Most of the configuration is done in the configmap :
 * Adapt your domain name and app name
 * Adapt the POD network to match your CNI configuration (you will face IMAP and SMTP authentication problems if you don't)
 * Adapt the ingress with your own cluster issuer name, change the domain name here as well

Enjoy !
