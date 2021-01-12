# Bitnami Sealed Secrets - How To Store Kubernetes Secrets In Git


## Repo

- https://github.com/bitnami-labs/sealed-secrets  

## Setup

Helm
```
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secret
helm repo update
helm install sealed-secret sealed-secrets
```


Install kubeseal
```
# Mac
brew install kubeseal

# Linux
wget https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.12.4/kubeseal-linux-amd64 -O kubeseal
sudo install -m 755 kubeseal /usr/local/bin/kubeseal
```



## Usage


```
kubectl --namespace default create secret generic mysecret --dry-run=client --from-literal foo=bar --output json | kubeseal | tee mysecret.yaml
kubectl create -f mysecret.yaml
```


