# Installing Helm on Jenkins server

## Add Jenkins user into sudoers file to get sudo access

```sh
vi /etc/sudoers
jenkins ALL=(ALL) NOPASSWD: ALL
```

```sh
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh -v v2.14.1
```
# Installing Tiller

## Create a tiller Serviceaccount in Kubernetes Master

```sh
kubectl -n kube-system create serviceaccount tiller
```
## Bind the tiller serviceaccount to the cluster-admin role in Kubernetes Master:

```sh
kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
```

## Copy admin.conf file from Kubernetes master to Jenkins user's home directory in Jenkins server

```sh
mkdir /var/lib/jenkins/.kube
Manually copy /etc/kubernetes/admin.conf file to /var/lib/jenkins/.kube/config file

chown -R jenkins:jenkins /home/jenkins/.kube
```

## Run 'helm init' in Jenkins Server to configure helm

```sh
helm init --service-account tiller
```
