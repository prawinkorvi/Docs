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
            cpu: '1'
            memory: 1Gi
          requests:
            cpu: '1'
            memory: 1Gi
  ```
## Install siege package inside the Application Pod
```sh
apt-get update
apt-get install siege
```

siege -q -c 5 -t 2m http://ip:port
