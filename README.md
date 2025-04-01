# Homelab
Homelab set up 

1. Pre-requisits 
1.1 Install Docker
1.2 Install minikube
1.3 Install kubctl
1.4 Install helm
1.5 conntrack
VERSION="v1.30.0" # check latest version in /releases page
wget https://github.com/kubernetes-sigs/cri-tools/releases/download/$VERSION/crictl-$VERSION-linux-amd64.tar.gz
sudo tar zxvf crictl-$VERSION-linux-amd64.tar.gz -C /usr/local/bin
rm -f crictl-$VERSION-linux-amd64.tar.gz

2. Starting Cluster
cmd: minikube start --cpus 4 --memory 8192 --driver=docker
minikube start --driver=none --apiserver-ips=192.168.88.232 --apiserver-name=homelab


3. Installing charts

3.1 Prometheus and Grafana
cmd: helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
cmd: helm repo update
cmd: helm install prometheus prometheus-community/kube-prometheus-stack

Wait for the pods to be span up
Port forward the UIs so it is accessable.
cmd: kubectl port-forward --address 0.0.0.0 service/prometheus-kube-prometheus-prometheus 9090


