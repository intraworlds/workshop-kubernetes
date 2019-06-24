# IWorkshop - Úvod do Kubernetes

## Úkoly
Tentokrát jsou dobrovolné úkoly velmi snadné. Cílem je hlavně vyzkoušet si, že
nástup do Kubernetes je velmi snadný. Nainstalovat lokální cluster a spustit
první _Hello World_ aplikaci Vám zabere okolo pěti minut (plus čas na stažení).

Bonusový úkol vyžaduje už trochu elaborace, ale také lze vyřešit s pomocí
dokumentace během několika desítek minut.

### Nainstalujte lokální kubernetes cluster
Použijte nástroj [Minikube], který vytvoří prostředí pro Docker a pustí potřebné
Kubernetes komponenty jako běžné kontejnery.

Pokračujte dle následujícího [https://kubernetes.io/docs/tasks/tools/install-minikube/](návodu)

### Spusťte Hello World aplikaci
Create a Kubernetes Deployment which is responsible for application's Pod health
```console
$ kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
deployment.apps/hello-node created
```
View the Deployment
```console
$ kubectl get deployments
NAME         READY   UP-TO-DATE   AVAILABLE   AGE
hello-node   1/1     1            1           5s
```
View the Pod
```console
$ kubectl get pods
NAME                          READY   STATUS    RESTARTS   AGE
hello-node-78cd77d68f-khtnm   1/1     Running   0          10s
```
View cluster events
```console
$ kubectl get events
```
View the `kubectl` configuration
```console
$ kubectl config view
```

Create a Service which exposing the Pod to the Internet
```console
$ kubectl expose deployment hello-node --type=LoadBalancer --port=8080
service/hello-node exposed
```

View the Service you just created
```console
$ kubectl get services
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
hello-node   LoadBalancer   10.100.41.161   <pending>     8080:32491/TCP   90s
kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          4d4h
```

Open hello world app in browser
```console
$ minikube service hello-node
🎉  Opening kubernetes service default/hello-node in default browser...
```

### Bonus: Nainstaluj Wordpress cluster
__TODO__



[Minikube]: https://kubernetes.io/docs/tasks/tools/install-minikube/
