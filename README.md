# prom-grafana

## This is how to deploy grafana and promethues helm charts

## Deploy Grafana 
```
cd grafana
kubectl create namespace monitoring
helm install --name release1 --namespace monitoring .
```



## Deploy prometheus 
```
cd prometheus
kubectl create namespace monitoring
helm install --name release2 --namespace monitoring .
```


- if you need to modify the retention period just modify the values.yaml file and modify the 
```
  prometheusSpec:
    retention: 35d
```
```
helm upgrade release2 .
```

## install Helm and Tiller

```
curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > install-helm.sh
chmod u+x install-helm.sh
./install-helm.sh

kubectl -n kube-system create serviceaccount tiller
kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
helm init --service-account tiller
```

## kubectl
```
kubectl get po -o wide
kubectl get nodes
kubectl get daemonsets.

kubectl port-forward svc/release-prometheus-operato-prometheus 9090:9090
```





# Docker Images
```
docker pull quay.io/coreos/prometheus-operator:v0.35.0
docker pull squareup/ghostunnel:v1.5.2
docker pull quay.io/coreos/prometheus-config-reloader:v0.35.0
docker pull quay.io/coreos/configmap-reload:v0.0.1
docker pull jettech/kube-webhook-certgen:v1.0.0
docker pull quay.io/coreos/kube-state-metrics:v1.9.3
docker pull quay.io/prometheus/prometheus:v2.15.2
docker pull quay.io/prometheus/alertmanager:v0.20.0
docker pull quay.io/prometheus/node-exporter:v0.18.1


docker tag quay.io/coreos/prometheus-operator:v0.35.0 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus-operator
docker tag squareup/ghostunnel:v1.5.2 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:ghostunnel
docker tag quay.io/coreos/prometheus-config-reloader:v0.35.0 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus-config-reloader
docker tag quay.io/coreos/configmap-reload:v0.0.1 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:configmap-reload
docker tag jettech/kube-webhook-certgen:v1.0.0 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:kube-webhook-certgen
docker tag quay.io/coreos/kube-state-metrics:v1.9.3 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:kube-state-metrics
docker tag quay.io/prometheus/prometheus:v2.15.2 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus
docker tag quay.io/prometheus/alertmanager:v0.20.0 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:alertmanager
docker tag quay.io/prometheus/node-exporter:v0.18.1 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:node-exporter



docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus-operator
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:ghostunnel
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus-config-reloader
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:configmap-reload
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:kube-webhook-certgen
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:kube-state-metrics
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:prometheus
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:alertmanager
docker push 261527745982.dkr.ecr.us-east-1.amazonaws.com/test:node-exporter

```

























