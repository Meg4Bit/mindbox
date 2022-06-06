# Stand for Kubernetes

Tested on Windows 10 Home using Minikube with Docker Desktop.

To start Minikube:

	minikube start --driver=docker

When minikube starts, Metrics Server should be configured.

	minikube addons enable metrics-server
	kubectl -n kube-system rollout status deployment metrics-server

If Metrics Server does't work properly, it can be fixed using file `metrics-fix.yaml`:

	kubectl delete clusterrole system:heapster
	kubectl apply -f metrics-fix.yaml

To start service use following command:

	kubectl apply -f mindbox.yaml