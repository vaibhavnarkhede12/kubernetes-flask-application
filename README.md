# kubernetes-flask-application

1. hope you have a docker image created using https://github.com/vaibhavnarkhede12/docker-flask-application repo
2. minikube image load flask:0.1   // this is to ensure minkube uses image from our local docker instead of hitting dockerhub also note imagePullPolicy: Never in kflask.yaml for same 
3. kubectl apply -f flask-service.yaml
4. kubectl apply -f flask.yaml
5. minikube service kflask-service
