# Go Demo 4 - Go Demo application in Istio Service Mesh

Using Istio with Golang app

# Table of Contents
1. [Deploy the application example](#deploy-the-application-example)
2. [Create Gateway & VirtualService Istio objects](#create-gateway--virtualservice-istio-objects)

## Deploy the application example

### Deploy the application

Before deploy the application, create namespace `demo`:

```sh
kubectl create namespace demo
```

Enable Istio sidecar injection by default:

```sh
kubectl label namespace demo istio-injection=enabled
```

Deploy Go Demo Application:

```sh
kubectl apply -f k8s/configmap.yaml

kubectl apply -f k8s/deploy.yaml

kubectl apply -f k8s/service.yaml
```

### Create Gateway & VirtualService Istio objects

```sh
kubectl apply -f k8s/configmap.yaml

kubectl apply -f k8s/deploy.yaml

kubectl apply -f k8s/service.yaml
```

Check:

sh```
URL=$(kubectl get svc istio-ingressgateway -n istio-system -o jsonpath='{.status.loadBalancer.ingress[0].ip}')

curl http://$URL/isAlive -H "Host: <CHANGE_WITH_YOUR_DNS>"
```