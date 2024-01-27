### Install microk8s 
```
sudo snap install microk8s --classic --channel=1.28
sudo usermod -a -G microk8s $USER
sudo chown -f -R $USER ~/.kube
microk8s status --wait-ready
```
### Enable Addons
```
microk8s enable dns
microk8s enable helm
microk8s enable helm3
microk8s enable community
microk8s enable metrics-server
```
### Install cert-manager CRD's
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.3/cert-manager.crds.yaml
```
### Add helm repo for cert-manager
```
helm repo add jetstack https://charts.jetstack.io
```
### Install cert-manager helm chart
```
helm install cert-manager --namespace cert-manager --version v1.13.3 jetstack/cert-manager --create-namespace
```
### Add flink kubernetes operator repo and install flink kubernetes operator - latest version 1.7.0
```
helm repo add flink-operator-repo https://downloads.apache.org/flink/flink-kubernetes-operator-1.7.0
```
### Create namespace for flink cluster components
```
kubectl create ns flink-cluster
```
### Install flink kubernetes operator
```
helm install flink-kubernetes-operator flink-operator-repo/flink-kubernetes-operator -n flink-cluster
```
### Deploy flink Job manager
```
kubectl apply -f flink.yml
```
###### Install Apache Kafka
```
helm install kafka oci://registry-1.docker.io/bitnamicharts/kafka --create-namespace
```
### Enable OPENEBS Storage class
```
microk8s enable openebs
``` 
### Set default storage class 
### to openebs-device/openebs-device (For single node microk8s)
```
sudo systemctl enable iscsid
kubectl patch storageclass openebs-device -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```
### Else enable hostpath storage addon (core) Storage class; allocates storage from host directory
```
microk8s enable hostpath-storage     
```
### to openebs-jiva-csi-default (For multi node microk8s cluster)
```
sudo systemctl enable iscsid
kubectl patch storageclass openebs-jiva-csi-default -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```
