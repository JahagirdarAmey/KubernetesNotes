[Pods](https://kodekloud.com/p/practice-test-kubernetes-ckad-pods)

<details><summary>How many PODs exist on the system?</summary>

```yaml
k get pods
```

</details>

<details><summary>Create a new pod with the NGINX image</summary>

```yaml
k run pod --image=nginx
```

</details>   

<details><summary>How many pods are created now?</summary>

```yaml
k get pods
```

</details>

<details><summary>Which image is used to create a new pods</summary>

```yaml
k describe pods newpods-lf26b
```

</details>

<details><summary>Which nodes are these pods placed on?</summary>

```yaml
k get pods -o=wide
```

</details>

<details><summary>How many containers are part of the pod 'webapp'?</summary>

```yaml
k describe pods webapp
```

</details>

<details><summary>What images are used in the new 'webapp' pod?</summary>

```yaml
k describe po webapp
```

</details>

<details><summary>What is the state of the container 'agentx' in the pod 'webapp'?</summary>

```yaml
k describe po webapp
```

</details>

<details><summary>Why do you think the container 'agentx' in pod 'webapp' is in error?</summary>

```yaml
k describe po webapp
```

</details>

<details><summary>Delete the 'webapp' Pod.</summary>

```yaml
k delete po webapp
```

</details>

<details><summary>Create a new pod with the name 'redis' and with the image 'redis123'</summary>

```yaml
k run redis --image=redis123 --generator=run-pod/v1
``` //TODO

</details>

<details><summary>Now fix the image on the pod to 'redis'.</summary>

```yaml
k edit po redis
```

</details>

[ReplicaSets](https://kodekloud.com/p/practice-test-kubernetes-ckad-replicasets)

<details><summary>How many ReplicaSets exist on the system?</summary>

```yaml
k get rs
```

</details>
    
<details><summary>How many PODs are DESIRED in the new-replica-set?</summary>

```yaml
k get rs
```
Look at desired 
</details>
    
<details><summary>What is the image used to create the pods in the new-replica-set?</summary>

```yaml
k describe rs
```
</details>
    
<details><summary>How many PODs are READY in the new-replica-set?</summary>

```yaml
k get rs
```
 
Look at ready column</details> 
   
<details><summary>Delete any one of the 4 PODs</summary>

```yaml
k delete po new-replica-set-kfgml
```
</details>
    
<details><summary>How many PODs exist now?</summary>

```yaml
k get po
```

</details>
    
<details><summary>Why are there still 4 PODs, even after you deleted one?</summary>     
New pod created automatically when deleted one. RS ensures desired number of pods</details> 
    
<details><summary>Create a ReplicaSet using the 'replicaset-definition-1.yaml' file located at /root/</summary>

```yaml
kubectl create -f FILENAME 
```

</details>
    
<details><summary>Fix the issue in the replicaset-definition-2.yaml file and create a ReplicaSet using it.</summary>
Lables should match, API Version </details>
    
<details><summary>Delete the two newly created ReplicaSets - replicaset-1 and replicaset-2</summary>

```yaml
k delete rs name
```

</details>
    
<details><summary>Fix the original replica set 'new-replica-set' to use the correct 'busybox' image **IMP**</summary>
     
```yaml
k edit rs new-replica-set.
```
   
Delete all pods 
</details>
 
<details><summary>Scale the ReplicaSet to 5 PODs</summary>

```yaml
k edit rs new-replica-set
```

</details>
    
<details><summary>Now scale the ReplicaSet down to 2 PODs</summary>
k edit rs new-replica-set //TODO </details>
    
[Deployements](https://kodekloud.com/p/practice-test-kubernetes-ckad-deployments)    

<details><summary>How many Deployments exist on the system?</summary>

```yaml
k get deploy 
```   

</details>
    
<details><summary>Out of all the existing PODs, how many are ready?</summary>

```yaml
k get po
Ready Column - 0/1
```   

</details>
    
<details><summary>What is the image used to create the pods in the new deployment?</summary>

```yaml
k get deploy -o=wide
```   

</details>
    
<details><summary>Why do you think the deployment is not ready?</summary>
Image does not exist</details>
    
<details><summary>Create a new Deployment using the 'deployment-definition-1.yaml' file located at /root/</summary>
kind, api version, labels, image  </details>

<details><summary>Create a new Deployment with the below attributes using your own deployment definition file Name: httpd-frontend, Replicas: 3, Image: httpd:2.4-alpine</summary>    

```yaml
kubectl run --generator=deployment/v1beta1 httpd-frontend --replicas=3 --image=httpd:2.4-alpine
```   

</details>
     
<details><summary>Create an NGINX Pod </summary>

```yaml
kubectl run --generator=run-pod/v1 nginx --image=nginx
```   

</details>

<details><summary>Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)</summary>

```yaml
kubectl run --generator=run-pod/v1 nginx --image=nginx --dry-run -o yaml
```   

</details>

<details><summary>Create a deployment</summary>

```yaml
kubectl run --generator=deployment/v1beta1 nginx --image=nginx
```   

</details>

<details><summary>Or the newer recommended way:</summary>

```yaml
kubectl create deployment --image=nginx nginx
```   

</details>

<details><summary>Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)</summary>

```yaml
kubectl run --generator=deployment/v1beta1 nginx --image=nginx --dry-run -o yaml
    Or
kubectl create deployment --image=nginx nginx --dry-run -o yaml
```   

</details>

<details><summary>Generate Deployment YAML file (-o yaml). Don't create it(--dry-run) with 4 Replicas (--replicas=4)</summary>

```yaml
kubectl run --generator=deployment/v1beta1 nginx --image=nginx --dry-run --replicas=4 -o yaml
```   

</details>

<details><summary>kubectl create deployment does not have a --replicas option. You could first create it and then scale it using the kubectl scale command.</summary></details>

<details><summary>Save it to a file - (If you need to modify or add some other details)</summary>

```yaml
kubectl run --generator=deployment/v1beta1 nginx --image=nginx --dry-run --replicas=4 -o yaml > nginx-deployment.yaml
```   

</details>


<details><summary>Create a Service named nginx of type NodePort and expose it on port 30080 on the nodes:</summary>

```yaml
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run -o yaml
```   

</details>
      
  
[Commands](https://kodekloud.com/p/practice-test-kubernetes-cka-imperative-1)   

<details><summary>Deploy a pod named nginx-pod using the nginx:alpine image.</summary>

```yaml
k run  --generator=run-pod/v1 nginx-pod --image=nginx:alpine
```

</details>
   
<details><summary>Deploy a redis pod using the redis:alpine image with the labels set to tier=db</summary>   

```yaml
k run  --generator=run-pod/v1 redis --labels=tier=db --image=redis:alpine
```

</details>

<details><summary>Create a service redis-service to expose the redis application within the cluster on port 6379.</summary>

```yaml
k expose pod redis --port=6379 --name redis-service
```

</details>
  
<details><summary>Create a deployment named webapp using the image kodekloud/webapp-color with 3 replicas</summary>

```yaml
k run --generator=deployment/v1beta1 webapp --image=kodekloud/webapp-color --replicas=3  
```

</details>
    
<details><summary>Expose the webapp as service webapp-service application on port 30082 on the nodes on the cluster. The web application listens on port 8080</summary>

```yaml
kubectl expose deployment webapp --type=NodePort --port=8080 --name=webapp-service --dry-run -o yaml > webapp-service.yaml
```

</details>
    
[Namespaces](https://kodekloud.com/p/practice-test-kubernetes-ckad-namespaces)

<details><summary>How many Namespaces exist on the system?</summary>

```yaml
kubectl get namespace
```

</details>


<details><summary>How many pods exist in the 'research' namespace?</summary>

```yaml
kubectl get namespace
```

</details>

<details><summary>Create a POD in the 'finance' namespace.?</summary>

```yaml
k run redis --image=redis --namespace=finance --generator=run-pod/v1
```

</details>


<details><summary>Which namespace has the 'blue' pod in it?</summary>

```yaml
kubectl get pods --all-namespaces
```

</details>

<details><summary>Access the Blue web application using the link above your terminal</summary>

```yaml
TODO
```

</details>

<details><summary>Access the Blue web application using the link above your terminal</summary>

```yaml
TODO
```

</details>

<details><summary>What DNS name should the Blue application use to access the database 'db-service' in its own namespace - 'marketing'.</summary>

```yaml
TODO
```

</details>

<details><summary>What DNS name should the Blue application use to access the database 'db-service' in the 'dev' namespace</summary>

```yaml
TODO
```

</details>





## Common Error Messages

```yaml
master $ k describe newpods-9dqvd
error: the server doesn't have a resource type "newpods-9dqvd"
```

```yaml
#Error from server (BadRequest): error when creating deployment-definition-1.yaml: deployment in version "v1" cannot be handled as a Deployment: no kind "deployment" is registered for version "apps/v1"
```

## Time savers
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
