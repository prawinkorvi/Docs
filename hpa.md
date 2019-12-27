# Configure Horizontal Pod Autoscaler

## Modify deployment.yaml with Resource limits
  strategy:
    type: RollingUpdate
    rollingUpdate:
    maxSurge: 0
    maxUnavailable: 1
  minReadySeconds: 5
  revisionHistoryLimit: 10
  
## Install siege package inside the Application Pod
apt-get update
apt-get install siege

siege -q -c 5 -t 2m http://ip:port
