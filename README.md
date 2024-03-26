# kubernetes-flask-application

1. hope you have a docker image created using https://github.com/vaibhavnarkhede12/docker-flask-application repo
2. minikube start --vm-driver=docker
3. minikube dashboard // This will open up the kubernetes UI on your browser
3. minikube image load flask:0.1   // this is to ensure minkube uses image from our local docker instead of hitting dockerhub also note imagePullPolicy: Never in kflask.yaml for same 
4. kubectl apply -f flask-service.yaml
5. kubectl apply -f flask.yaml
6. minikube service kflask-service

