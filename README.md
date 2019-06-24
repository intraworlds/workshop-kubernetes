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
```console
# create a Kubernetes Deployment which is responsible for application's Pod health
$ kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
deployment.apps/hello-node created

# view the Deployment
$ kubectl get deployments
NAME         READY   UP-TO-DATE   AVAILABLE   AGE
hello-node   1/1     1            1           5s

# view the Pod
$ kubectl get pods
NAME                          READY   STATUS    RESTARTS   AGE
hello-node-78cd77d68f-khtnm   1/1     Running   0          10s

# view cluster events
$ kubectl get events

# view the `kubectl` configuration
$ kubectl config view


# create a Service

# expose the Pod to the public internet
$ kubectl expose deployment hello-node --type=LoadBalancer --port=8080
service/hello-node exposed


# view the Service you just created
$ kubectl get services
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
hello-node   LoadBalancer   10.100.41.161   <pending>     8080:32491/TCP   90s
kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          4d4h

# open hello world app in browser
$ minikube service hello-node
🎉  Opening kubernetes service default/hello-node in default browser...
```

### Bonus: Nainstaluj Wordpress cluster
__TODO__



[Minikube]: https://kubernetes.io/docs/tasks/tools/install-minikube/
