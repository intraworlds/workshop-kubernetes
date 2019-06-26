```console
$ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080
deployment.apps/hello-minikube created

$ kubectl expose deployment hello-minikube --type=NodePort
service/hello-minikube exposed

$ kubectl get pod
NAME                              READY   STATUS              RESTARTS   AGE
hello-minikube-56cdb79778-7b2wk   0/1     ContainerCreating   0          23s

$ minikube service hello-minikube --url
http://192.168.99.101:31960
```
