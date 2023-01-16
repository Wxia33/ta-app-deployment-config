# TA App Deployment config and learnings

# Kubernetes config

Run app in kubernetes for scaling

nginx
frontend
backend (api routing to ai endpoints)
backend (ai endpoints (optional))

## Minkube

minkube start --vm-driver=hyperkit https://minikube.sigs.k8s.io/docs/start/

minikube pause
minikube unpause

kubectl get po -A  
kubectl get services
kubectl get pods
kubectl get services
kubect get namespaces

minikube dashboard

kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
minikube service hello-node 

minikube addons enable metrics-server  

https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

minikube addons enable ingress 

kubectl create deployment demo --image=httpd --port=80             17:29:32
kubectl expose deployment demo

kubectl create ingress demo-localhost --class=nginx \              17:29:32
  --rule="demo.localdev.me/*=demo:80"

kubectl port-forward --namespace=ingress-nginx service/ingress-nginx-controller 8080:80

Ingress is an api object used to manage external access to services in cluster
https://kubernetes.io/docs/concepts/services-networking/ingress/

Running ingress-nginx
https://github.com/kubernetes/ingress-nginx
Ingress-nginx is ingress controller for kubernetes using nginx as reverse proxy and load balancer

TODO: how to point ingress/configure nginx to run specific endpoints and services?


# Arch
