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