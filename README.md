# kub-exp

## Tools

* [Minicube](https://kubernetes.io/docs/setup/minikube/) - Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.
  * [Minicube installation](https://kubernetes.io/docs/tasks/tools/install-minikube/)
  * [Minikube KVM2 driver](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#kvm2-driver)

## Tutorials

* [kubeconfig file](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/)

## Snippets

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

Start docker image:

```
kubectl run statsd-http-proxy --port 80 --image=gometric/statsd-http-proxy:latest
kubectl expose deployment statsd-http-proxy
```

