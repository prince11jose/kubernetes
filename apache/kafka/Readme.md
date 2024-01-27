### Add Bitnami charts repo
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
### Install Apache Kafka
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
