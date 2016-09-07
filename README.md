# ex-gke-webdrop
Example Kubernetes (GKE) Deploy

## Cheet Sheet

```
> docker build –t gcr.io/$PROJECT_ID/webdrop:v1 .
> gcloud docker push gcr.io/$PROJECT_ID/webdrop:v1

> gcloud container clusters create <cluster-name: webdrop-cluster>
> gcloud container clusters get-credentials <cluster-name>
```

### Deploy

```
> kubectl run <deploy-name: webdrop> \
    --image=gcr.io/$PROJECT_ID/webdrop:v1 \
    --port=5000

> kubectl create –f webdrop-deploy.yaml
```

### Introspect

```
> kubectl get deployments | pods | services  [thing-name]
> kubectl get events
> kubectl cluster-info
> kubectl config view
> kubectl logs <pod-name>
```

### External Access

```
> kubectl expose deployment <deploy-name: webdrop> --type=”LoadBalancer”
> kubectl get services [<service-name: webdrop>]
```

### Clean-up

```
> kubectl delete service,deployment <deployment-name>
> gcloud container clusters delete <cluster-name>
```
