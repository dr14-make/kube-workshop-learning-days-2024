## Installing necessery tools

``` shell
brew install minikube kubectl helm derailed/k9s/k9s lens
```

Start your cluster
From a terminal with administrator access (but not logged in as root), run:

``` shell
minikube start
```

To startup minikube on boot you can follow the following [instructions](https://joepreludian.medium.com/how-to-start-up-minikube-automatically-via-system-d-2cad99fd79bf)

### Lets see what we got so far

``` shell
kubectl config get-contexts
```

### Set the minikube context if you have more

``` shell
kubectl config set-context minikube
```
