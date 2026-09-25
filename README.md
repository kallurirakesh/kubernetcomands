docker ps
docker images 
docker pull mongo
docker run -d -p 27017:27017 --name product-mongo mongo

>docker logs -f product-mongo
docker exec -it product-mongo /bin/bash
ls
mongosh
show dbs
use ProductsDb
db.createCollection('Products')

docker stop 03ec96d8a16e -- to stop containers

docker rm 03ec96d8a16e -- to remove container 

docker ps -a  -- hidden containers


docker compose -f docker-compose.yml -f docker-compose.override.yml down/up
>docker tag c7430a029667 kallurirakesh/productsapi:latest
docker login 
>docker push kallurirakesh/productsapi:latest
docker rmi 50be6a766d26 -f
---- 

Kubernetes

------
•	apiVersion: apps/v1 — Deployment API group/version.
•	kind: Deployment — creates a Deployment controller (manages ReplicaSets/Pods).
•	metadata.name: nginx-deployment — resource name.
•	metadata.labels — labels applied to the Deployment object.
•	spec:
•	replicas: 1 — desired number of pod replicas (one pod).
•	selector.matchLabels — label selector that ties the Deployment to pods (must match template.metadata.labels).
•	template:
•	metadata.labels — labels applied to pods created by this Deployment.
•	spec.containers — container spec for the Pod:
•	name: nginx
•	image: nginx:latest — image used for the container.
•	ports — exposes container port 80 inside the pod.
minikube start

>kubectl get pod
>kubectl get deployment
>kubectl get services
kubectl get all
>kubectl delete service productservice-release

kubectl create deployment nginx-depl --image=nginx
kubectl edit deployment nginx-depl
kubectl logs nginx-depl-569bd7dcf9-pwgrj
kubectl describe pod nginx-depl-569bd7dcf9-pwgrj
Kubectl apply -f .\nginx-deploy.yaml
kubectl get deployment nginx-depl -o yaml

kubectl get secrets

kubectl describe service monogdb-service 
ubectl get pod mongo-deployment-68bb947c68-f8tzq -o wide
