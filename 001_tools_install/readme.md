We are mostly going to use helm to install the applicatinons \.
## Installing necessery tools
```warp-runnable-command
brew install minikube kubectl helm derailed/k9s/k9s lens
```
Start your cluster
From a terminal with administrator access \(but not logged in as root\)\, run\:
```warp-runnable-command
minikube start
```
To startup minikube on boot you can follow the following [instructions](https://joepreludian.medium.com/how-to-start-up-minikube-automatically-via-system-d-2cad99fd79bf)
### Lets see what we got so far
```warp-runnable-command
kubectl config get-contexts
```
### Set the minikube context if you have more
```warp-runnable-command
kubectl config set-context minikube
```
We have the cluster now\, but it is only avaliable from this machine but we want to be able to install applications to the cluster from anywhere\.\.\.\. Argocd to the rescue

## Lets install argocd

### **What** **is Argo CD\?**

[Argo CD](https://argoproj.github.io/argo-cd/) is a [GitOps](https://www.gitops.tech/) tool to automatically synchronize the cluster to the desired state defined in a Git repository\. Each workload is defined declarative through a resource manifest in a YAML file\. Argo CD checks if the state defined in the Git repository matches what is running on the cluster\, and synchronizes it if changes were detected\.

```warp-runnable-command
helm repo add argo https://argoproj.github.io/argo-helm
helm dep update charts/argocd
helm install argocd charts/argo-cd/ --namespace argocd --create-namespace

```
Getting  the initial secret

```warp-runnable-command
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d


```
Exposing the argo outside the service manually for now
```warp-runnable-command
kubectl port-forward svc/argo-cd-argocd-server -n argocd 8080:443
```
