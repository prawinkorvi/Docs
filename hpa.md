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
## hpa.yaml file in helm chart
 ```sh
  apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
  name: petclicnic-hpa
spec:
  maxReplicas: 5
  minReplicas: 1
  scaleTargetRef:
    apiVersion: extensions/v1beta1
    kind: Deployment
    name: petclinic-deployment
  targetCPUUtilizationPercentage: 20
  ```
## Install siege package on K8 Master

### Siege is a stress tester for HTTP/HTTPS

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
