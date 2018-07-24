# kubernetes-demo

1. Kubernetes abbrevated k8s
2. Kubernetes Auto-scaling, cloud-agnostic yet integrable technologies.
3. Docker-Swarm, Apache Mesos are another orchesteration.
4. Kubernetes runs anywhere Linux does.
  a. Your laptop
  b. Globally distributed data centers.
  c. Major cloud providers
  d. Anywhere in between & nearly any combination (not that you'd want to necessarily)
5. @Question: What is "Network Load Balancer", "Application load balancer"
6. minikube is good for Evaluating, Training and Development purpose with kubernetes.
7. @Question: How to use kops for setting up kubernetes on AWS.
8. Kops is a tool for production greade k8s installation, upgrades and management.
9. Kubernetes "Deployments" these are high level constructs that defines an application. 
10. A Pod is the instance of docker container, Deployments can have any number of pods required to get the job done. 
11. "Services" are endpoints that expose ports to the outside world.
12. You can create, delete, modify and retereve information about any of these using the kubectl command (as well as the Kubernetes local UI)
13. run kubctl
```
kubectl run hello-minikub
e --image=gcr.io/google_containers/echoserver:1.10
--port=8080
```
14. Expose service
```
kubectl expose deployment hello-minikube --type=NodePort
```
15. @Question: Type type of other services are available in k8s as --type=NodePort
16. --type=NodePort allow us to have external IP address connected to the port of container that we just created.
17. Command to get running pods
```
kubectl get pod
```
That will get you Name, Age, Current Status of the pods.
18. get url of the service with minikube
```
minikube service hello-minikube --url
```
19. To delete the deployment hello-minikube
```
kubectl delete deployment hello-minikube
```
20. To stop minikube instance.
```
minikube stop
```
That will stop virtual machine running in virtual box.

21. Deployments
  a. "Deployments" are the central metaphor for what we'd consider "app" or "services"
  b. Deployments are described as a collection of resources and references.
  c. Deployments take many forms based on the type of services being deployed. 
  d. Typically described in YAML format.

22. Apply deployments
```
kubectl apply deployment.yml
```
Make sure your VM is running while executing this command.
23.
