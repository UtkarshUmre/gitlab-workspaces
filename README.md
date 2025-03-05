# gitlab-workspaces

Creating a Kubernetes Cluster on Google Cloud

```bash
gcloud container clusters create estenrebuk \
  --enable-autoscaling \
  --num-nodes=3 \
  --min-nodes=1 \
  --max-nodes=5 \
  --machine-type=e2-standard-2 \
  --disk-type=pd-standard \
  --disk-size=10

```

Install Flux in Kubernetes cluster

```bash
flux bootstrap gitlab \
  --owner=GITLAB_USERNAME_OR_GROUP \
  --repository=REPO_NAME \
  --branch=main \
  --path=./clusters/estenrebuk \
  --token-auth

```

Verify Flux Installation


```bash
kubectl get pods -n flux-system
```

Check Flux Status

```bash
flux check
```

