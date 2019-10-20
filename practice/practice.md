# Recap Core Concepts 

## Pods 

<details><summary>How many PODs exist on the system? in the current(default) namespace</summary>

```yaml
kubectl get pods
```

</details>

<details><summary>Create a new pod with the NGINX image</summary>

```yaml
kubectl run nginx --image=nginx
```

</details>

<details><summary>What is the image used to create the new pods?</summary>

```yaml
kubectl describe pods
```

</details>

<details><summary>Which nodes are these pods placed on?</summary>

```yaml
kubectl describe pods
```

</details>

<details><summary>How many containers are part of the pod 'webapp'?Note: We just created a new POD. Ignore the state of the POD for now.</summary>

```yaml
kubectl describe pod webapp
```

</details>


<details><summary>What images are used in the new 'webapp' pod? You must look at all the pods in detail to figure this out</summary>

```yaml
kubectl describe pod webapp
```

</details>

<details><summary>What is the state of the container 'agentx' in the pod 'webapp'? Wait for it to finish the 'ContainerCreating' state</summary>

```yaml
kubectl describe pod webapp
```

</details>

<details><summary>Why do you think the container 'agentx' in pod 'webapp' is in error? Try to figure it out from the events section of the pod</summary>

```yaml
Image does not exist on docker
```

</details>

<details><summary>What does the READY column in the output of the 'kubectl get pods' command indicate?</summary>

```yaml
Running containers in a pod / Total containers in a pod
```

</details>

<details><summary>Delete the 'webapp' Pod. Once deleted, wait for the pod to fully terminate.</summary>

```yaml
kubectl delete pod webapp
```

</details>

<details><summary>Create a new pod with the name 'redis' and with the image 'redis123'.</summary>

```yaml
kubectl run redis --image=redis123 --generator=run-pod/v1 
```

</details>

<details><summary>Create a new pod with the name 'redis' and with the image 'redis123'.</summary>

```yaml
kubectl edit pod redis
```

</details>


## ReplicaSets

<details><summary>How many ReplicaSets exist on the system?</summary>

```yaml
kubectl get replicaset
```

</details>

<details><summary>How many PODs are DESIRED in the new-replica-set?</summary>

```yaml
kubectl get replicaset
```

</details>

<details><summary>What is the image used to create the pods in the new-replica-set?</summary>

```yaml
kubectl describe replicaset
```

</details>

<details><summary>How many PODs are READY in the new-replica-set?</summary>

```yaml
kubectl get replicaset # just like pods 
```

</details>

<details><summary>Why do you think the PODs are not ready?</summary>

```yaml
Image busybox77 does not exist 
```

</details>

<details><summary>Delete any one of the 4 PODs</summary>

```yaml
kubectl get pods 
kubectl delete pod new-replica-set-j5th7
```

</details>

<details><summary>How many pods exists now</summary>

```yaml
same as before as replicasets ensure the number of pods 
```

</details>

<details><summary>Create a ReplicaSet using the 'replicaset-definition-1.yaml' file located at /root/</summary>

```yaml
Change api version and 
kubectl apply -f replicaset-definition-1.yaml
```

</details>

<details><summary>Fix the issue in the replicaset-definition-2.yaml file and create a ReplicaSet using it.</summary>

```yaml
The values for labels on lines 9 and 13 should match.
```

</details>

<details><summary>Delete the two newly created ReplicaSets - replicaset-1 and replicaset-2</summary>

```yaml
kubectl delete replicaset replicaset-1
kubectl delete replicaset replicaset-2
```

</details>

<details><summary>Fix the original replica set 'new-replica-set' to use the correct 'busybox' image. Either delete and re-create the ReplicaSet or Update the existing ReplicSet and then delete all PODs, so new ones with the correct image will be created.</summary>

```yaml
kubectl edit replicaset new-replica-set
```

</details>

<details><summary>Scale the ReplicaSet to 5 PODs</summary>

```yaml
kubectl edit replicaset new-replica-set
```

</details>

<details><summary>Now scale the ReplicaSet down to 2 PODs</summary>

```yaml
kubectl edit replicaset new-replica-set
```

</details>

## Deployements 

<details><summary>How many Deployments exist on the system?</summary>

```yaml
kubectl get deployements
```

</details>

<details><summary>Why do you think the deployment is not ready?</summary>

```yaml
Image does not exists
```

</details>

<details><summary>Create a new Deployment using the 'deployment-definition-1.yaml' file located at /root/</summary>

```yaml
kind: Deployement
```

</details>

<details><summary>Create a new Deployment with the below attributes using your own deployment definition file Name: httpd-frontend; Replicas: 3; Image: httpd:2.4-alpine</summary>

```yaml
kubectl run --generator=deployment/v1beta1 nginx --image=nginx --dry-run --replicas=4 -oyaml > some-name.yaml
```

</details>

##Namespaces

<details><summary>How many Namespaces exist on the system?</summary>

```yaml
kubectl get namespaces
```

</details>

<details><summary>How many pods exist in the 'research' namespace?</summary>

```yaml
kubectl get pods --namespace=research
```

</details>

<details><summary>Create a POD in the 'finance' namespace.</summary>

```yaml
kubectl run redis --image=redis --generator=run-pod/v1 --namespace=finance 
```

</details>

<details><summary>Which namespace has the 'blue' pod in it?</summary>

```yaml
kubectl get pods --all-namespaces
```

</details>

<details><summary>Access the blue application and ping it</summary>

```yaml
TODO
```

</details>

<details><summary>Access the blue application and ping it</summary>

```yaml
TODO
```

</details>


<details><summary>What DNS name should the Blue application use to access the database 'db-service' in its own namespace - 'marketing'.</summary>

```yaml
Same name
```

</details>

<details><summary>What DNS name should the Blue application use to access the database 'db-service' in the 'dev' namespace</summary>

```yaml
db-service.dev.svc.cluster.local
```

</details>

## Imperative Commands 


<details><summary>Deploy a pod named nginx-pod using the nginx:alpine image.</summary>

```yaml
kubectl run --generator=run-pod/v1 nginx-pod --image=nginx:alpine
```

</details>

<details><summary>Deploy a redis pod using the redis:alpine image with the labels set to tier=db.</summary>

```yaml
kubectl run --generator=run-pod/v1 redis --image=redis:alpine -l tier=db
```

</details>

<details><summary>Create a service redis-service to expose the redis application within the cluster on port 6379</summary>

```yaml
kubectl expose pod redis --port=6379 --name redis-service

TODO How
```

</details>

<details><summary>Create a deployment named webapp using the image kodekloud/webapp-color with 3 replicas</summary>

```yaml
kubectl create deployment webapp --image=kodekloud/webapp-color
kubectl scale deployment/webapp --replicas=3
TODO How
```

</details>

<details><summary>Expose the webapp as service webapp-service application on port 30082 on the nodes on the cluster</summary>

```yaml
kubectl expose pod redis --port=30082 --name webapp-service
```

</details>


[Commands and arguments]https://kodekloud.com/courses/kubernetes-certification-course-labs/lectures/12039454

<details><summary>What is the command used to run the pod 'ubuntu-sleeper'?</summary>

```yaml
kubectl describe pod
```

</details>

<details><summary>Create a pod with the ubuntu image to run a container to sleep for 5000 seconds. Modify the file ubuntu-sleeper-2.yaml.
Note: Only make the necessary changes. Do not modify the name.</summary>

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: ubuntu-sleeper-2
spec:
  containers:
  - name: ubuntu
    image: ubuntu
    command:
      - "sleep"
      - "1200"
```

</details>

<details><summary>Create a pod with the ubuntu image to run a container to sleep for 5000 seconds. Modify the file ubuntu-sleeper-2.yaml.
Note: Only make the necessary changes. Do not modify the name.</summary>

```yaml
Both sleep and 1200 should be defined as a string.
```

</details>

<details><summary>Update pod 'ubuntu-sleeper-3' to sleep for 2000 seconds.
Note: Only make the necessary changes. Do not modify the name of the pod. Delete and recreate the pod if necessary.</summary>

```yaml
Edit yaml
Delete pod
create pod 
```

</details>

<details><summary>Inspect the file 'Dockerfile' given at /root/webapp-color. What command is run at container startup?</summary>

```yaml
py app.py --color red 
```

</details>

<details><summary>Inspect the two files under directory 'webapp-color-2'. What command is run at container startup?
Assume the image was created from the Dockerfile in this folder</summary>

```yaml
kubernetes file overrides the dockerfile
```

</details>
<details><summary>Inspect the two files under directory 'webapp-color-3'. What command is run at container startup?
Assume the image was created from the Dockerfile in this folder</summary>

```yaml
#TODO Command in spec: needs to be clear
```

</details>


[ConfigMaps]https://2886795271-30099-kitek06j.environments.katacoda.com/#!/view1

<details><summary>What is the environment variable name set on the container in the pod?</summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

