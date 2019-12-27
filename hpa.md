# Configure Horizontal Pod Autoscaler

## Modify deployment.yaml with Resource limits
```sh
  strategy:
    type: RollingUpdate
    rollingUpdate:
    maxSurge: 0
    maxUnavailable: 1
  minReadySeconds: 5
  revisionHistoryLimit: 10
  
          resources:
          limits:
            cpu: "0.5"
            memory: "500Mi"
          requests:
            cpu: "0.5"
            memory: "500Mi"
  ```
## Install siege package on K8 Master
```sh
yum -y install epel-release
yum -y install siege
```
```sh
siege -q -c 2 -t 2m http://ip:port
q = quiet mode
c = concurrent
2m = time period
```
