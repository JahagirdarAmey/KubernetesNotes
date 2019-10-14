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
