#namespace --> config maps--> secrets --> pv --> pvc --> deployment --> service
Let's create pod first

#kubectl apply -f file.yml

kubectl apply -f pod-flask-app.yml

kubectl get pods

kubectl describe pod flask-app

#status: pending , so
docker pull imagename
kind load docker-image nginx --name my-first-cluster

kubectl
   ↓
API Server
   ↓
Scheduler
   ↓
Worker Node selected
   ↓
kubelet creates Pod
   ↓
Container runtime pulls image
   ↓
Container starts



kubectl apply -f namespace.yml

kubectl get ns

kubectl get pods

kubectl get pods -n flask-app

#to check if syntax is correct
kubectl apply -f deployment --dry-run

#to check deployment file name
kubectl get deployment -n flask-app

kubectl scale deployment flask-app-deployment --replicas=10 -n flask-app

kubectl get deployment -n flask-app

kubectl get pods -n flask-app

kubectl get all -n flask-app

kubectl port-forward svc/flask-app-service  8086:80 -n flask-app

kubectl decribe svc/flask-app-service -n flask-app


