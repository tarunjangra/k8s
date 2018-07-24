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
10. A Pod is the instance of docker container, Deployments can have any number of pods required to get the job done. It is a group of one or more containers with shared storage/network and other specification for how to run the container.
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
kubectl apply -f deployment.yml
```
Make sure your VM is running while executing this command.
23. Steps to get deployment working.
  a. Make sure your minikube instance is working in virtual box. else start this.
  ```
  minikube start
  ```
  b. apply deployment through <deployment>.yml file containing all information of the container being deployed.
  ```
  kubectl apply -f <deployment>.yml
  ```
  That will pull the container and make it in running stage
  c. Expose the port to get the access of choosen port
  ```
  kubectl expose deployment <deployment name> --type=NodePort
  ```
  d. Get the end of the service
  ```
  minikube service <deployment name> --url
  ```
  You are done
24. Get more detailed information about pod
```
kubectl describe pods <pod-name>
```
25. port-forward in kubectl
```
kubectl port-forward <pod-name> 5000:6000
```
25. kubectl attach allow you to get attached to a pod to view it's output. Attaches to a process that is already running inside an existing container.
```
kubectl attach <pod-name>
```
26. ssh your specific pod/container
```
kubectl exec -it <container-name-under-pod> bash
```
27. labeling pod container
```
kubectl label pods tomcat-deployment-56ff5c79c5-wt9sj healthy=false
```
28. run more then one replicas / containers in given deployment
```
kubectl scale --replicas=4 deployment/tomcat-deployment
```
29. Exposing loadbalancer
```
kubectl expose deployment tomcat-deployment --type=LoadBalancer --port=8080 --target-port=8080 --name tomcat-load-balancer
```
You can describe loadbalancer to get more details of loadbalancer
```
kubectl describe services tomcat-load-balancer
```
30. Deployments in more details
  a. Deployments are a high-level object in Kubernete, they define a desired state of an application.
  b. They Consist of pods.
  c. Optionally, they can also include ReplicaSets (that are automatically management by the Deployment based on it's replica configurations)

31. What you can do with deployment.
  a. Create new deployment.
  b. update created deployment.
  c. apply rolling updates to pods running on your cluster.
  d. Rollback to a previous version.
  e. Pause & Resume a deployment.

32. Get all deployments
```
kubctl get deployments
```
33. Get Status of deployment rollout
```
kubectl rollout status deployment <deployment-name>
```
34. To update the image of the deployment
```
kubectl set image deployment/tomcat-deployment tomcat=tomcate:9.0.1
```
Where tomcat is container name and tomcat:9.0.1 is tomcat container of specific version which need to be upgrade.
