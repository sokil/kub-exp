# kub-exp

## Tools

* [Minicube](https://kubernetes.io/docs/setup/minikube/) - Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.
  * [Minicube installation](https://kubernetes.io/docs/tasks/tools/install-minikube/)
  * [Minikube KVM2 driver](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#kvm2-driver)

## Tutorials

* [kubeconfig file](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/)
* [Web interface](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)

## Virtual machine

```
# GUI for virtual machines
apt install virt-manager
```

```
$ sudo virsh list --all
 Id    Name                           State
----------------------------------------------------
 -     minikube                       shut off

Start VM with minicube
$ sudo virsh start minikube

```

### Minikube

kubectl CLI autocomplete:

```
echo "source <(kubectl completion bash)" >> ~/.bashrc
```

Start minikube with kvm2 driver:

```
minikube start --vm-driver kvm2
```

Use kvm2 as a default driver:

```
minikube config set vm-driver kvm2
minikube start
```

## Pods

```
# Status of all pods
kubectl get pods --all-namespaces
```

## Staring images

Start docker image:

```
kubectl run statsd-http-proxy --port 80 --image=gometric/statsd-http-proxy:latest
kubectl expose deployment statsd-http-proxy
```

## UI

Manual: https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/

```
# Deploy dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml
# Create user
kubectl apply -f dashboard/dashboard-adminuser.yaml
# Get token
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```

Then open in browser: http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login
