# Adding the Istio Helm Repository
```
helm repo add istio https://istio-release.storage.googleapis.com/charts
helm repo update
```

# Installing Istio Base Chart
```
helm install istio-base istio/base -n istio-system --set defaultRevision=default --create-namespace
```

```
helm install istio-cni istio/cni -n istio-system 
helm install istiod istio/istiod -n istio-system  --values manifests/helm-profiles/demo.yaml --set pilot.cni.enabled=true

```

# Installing bookinfo

```
kubectl create namespace bookinfo
kubectl label namespace bookinfo istio-injection=enabled
kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml --namespace=bookinfo
```