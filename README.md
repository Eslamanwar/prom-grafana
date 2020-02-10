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





























