```console
$ kubectl apply -f redis-master-deployment.yaml
deployment.apps/redis-master created

$ kubectl get pods
$ kubectl logs -f POD-NAME

$ kubectl apply -f redis-master-service.yaml
service/redis-master created

$ kubectl apply -f redis-slave-deployment.yaml
deployment.apps/redis-slave created

$ kubectl apply -f redis-slave-service.yaml
service/redis-slave created

$ kubectl get service

$ kubectl apply -f frontend-deployment.yaml
deployment.apps/frontend created

$ kubectl get pods -l app=guestbook -l tier=frontend

$ kubectl apply -f frontend-service.yaml
service/frontend created

$ minikube service frontend --url
http://192.168.99.101:30108

$ kubectl scale deployment frontend --replicas=5
deployment.extensions/frontend scaled

$ kubectl delete service --all
$ kubectl delete deployment --all
```
