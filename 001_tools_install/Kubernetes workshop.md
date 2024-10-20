```warp-runnable-command
brew install minikube
brew install kubectl
brew install helm
brew install derailed/k9s/k9s

```
## **Start your cluster**
From a terminal with administrator access \(but not logged in as root\)\, run\:
```warp-runnable-command
minikube start

```
To startup minikube on boot you can follow the following [instructions](https://joepreludian.medium.com/how-to-start-up-minikube-automatically-via-system-d-2cad99fd79bf) 
# Lets see what we got so far
```warp-runnable-command
kubectl config get-contexts

```
## Set the minikube context if you have more
```warp-runnable-command
kubectl config set-context minikube
```
