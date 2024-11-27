##for install and uninstall##

Part1
docker build -t cymulate-assignment:latest ./Application
docker run -d -p 8080:8080 --name cymulate-container cymulate-assignment:latest

part2
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install mongodb bitnami/mongodb

helm list
helm uninstall cymulate-assignment

helm install cymulate-assignment ./Kubernetes/cymulate-assignment
minikube image load cymulate-assignment:latest  - If Using Local Kubernetes (Minikube or Docker Desktop)
helm upgrade cymulate-assignment ./Kubernetes/cymulate-assignment

kubectl get pods
kubectl logs -l app=cymulate-assignment

##for Debug##
kubectl get deployment
kubectl delete deployment cymulate-assignment
kubectl get pods
kubectl describe pod <pod name>

