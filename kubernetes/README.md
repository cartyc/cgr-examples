# Create KinD Cluster

For local testing you can use the provider [KinD](https://kind.sigs.k8s.io/) configs to get a cluster up and running. [Minikube](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Fx86-64%2Fstable%2Fbinary+download) should work as well but has not been tested. 

```
kind create cluster --config=kind.yaml
```

If you do not have a local cluster up and running and want to test images that are built locally you can use the following command to load the images into the KinD cluster.

```
kind load docker-image imagename:tag --name kindclustername
```