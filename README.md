# Metrics-Server Installation and Configuration

## Prerequisites

Add the Helm repo to the list of repo available locally:
```shell
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
```


## Local

To install locally, execute the following commands:
```shell
helm upgrade --install metrics-server metrics-server/metrics-server -n metrics-server --create-namespace -f base.values.yaml
```

To validate the installation is completed:
```shell
kubectl get pods -n metrics-server
```

To ensure there aren't any errors, using the pod name obtained from the previous command:
```shell
kubectl logs <POD_NAME> -n metrics-server 
```

To confirm the API has been added to the list of available API internally, execute the following command:
```shell
kubectl get apiservices.apiregistration.k8s.io
```

You should obtain a list containing the following line:
v1beta1.metrics.k8s.io                 metrics-server/metrics-server   True        16d

To use and obtain metrics of your cluster, use the following commands:
```shell
kubectl top nodes
kubectl top pods
```


## Sandbox




## References
1. https://youtu.be/qUW1tsSXCkQ?si=tmCFtVgroQ7nzCKb

 

## License

[Elastic License 2.0](./LICENSE) — source-available; not OSI open source.
