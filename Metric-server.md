# Metric server is required for Horizontal Pod Autoscaler

## What is Metric Server?
```sh
It collects metrics like CPU or memory consumption for containers or nodes, from the Summary API, exposed by Kubelet on each node.
```
## Clone Metric-server helm chart 
```sh
https://github.com/prawinkorvi/metric-server.git
```

## Create Metric Server
```sh
kubectl create -f .
kubectl top pods
kubectl top nodes
```

