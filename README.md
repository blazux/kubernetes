nano /etc/ssh/sshd_config permitroot=yes


Installer Docker

# apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common
# curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg | apt-key add -
# add-apt-repository "deb https://download.docker.com/linux/debian buster stable"
# apt-get update
# apt-get install -y docker-ce

Activez docker au démarrage :

systemctl enable docker

Configurez docker pour qu'il ne s'amuse qu'avec Systemd en créant le fichier /etc/docker/daemon.json :

root@k8snode1:/home/dada# nano /etc/docker/daemon.json
{
    "exec-opts": ["native.cgroupdriver=systemd"]
}

Et enfin, désactivez le swap avec la commande :

swapoff -a

Et commentez la ligne du nano /etc/fstab réactivant ce truc à chaque reboot :

# swap was on /dev/sda5 during installation
#UUID=5d159270-eaee-41ed-864c-711f242e044d none            swap    sw                                                     0       0

Installer Kubernetes

# curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
# add-apt-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
# apt-get update
# apt-get install -y kubelet kubeadm kubectl


kubeadm init --pod-network-cidr=192.168.0.0/16   
kubectl apply -f https://docs.projectcalico.org/v3.9/manifests/calico.yaml


 mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config




helm

kubectl -n kube-system create serviceaccount tiller

kubectl create clusterrolebinding tiller \
  --clusterrole=cluster-admin \
  --serviceaccount=kube-system:tiller

helm init --service-account tiller


https://get.helm.sh/helm-v2.14.3-linux-amd64.tar.gz





