# Recap Core Concepts 

## Pods 

<details>How many PODs exist on the system? in the current(default) namespace<summary></summary>

```yaml
kubectl get pods
```

</details>

<details>Create a new pod with the NGINX image<summary></summary>

```yaml
kubectl run nginx --image=nginx
```

</details>

<details>What is the image used to create the new pods?<summary></summary>

```yaml
kubectl describe pods
```

</details>

<details>Which nodes are these pods placed on?<summary></summary>

```yaml
kubectl describe pods
```

</details>

<details>How many containers are part of the pod 'webapp'?Note: We just created a new POD. Ignore the state of the POD for now.<summary></summary>

```yaml
kubectl describe pod webapp
```

</details>


<details>What images are used in the new 'webapp' pod? You must look at all the pods in detail to figure this out<summary></summary>

```yaml
kubectl describe pod webapp
```

</details>

<details>What is the state of the container 'agentx' in the pod 'webapp'? Wait for it to finish the 'ContainerCreating' state<summary></summary>

```yaml
kubectl describe pod webapp
```

</details>

<details>Why do you think the container 'agentx' in pod 'webapp' is in error? Try to figure it out from the events section of the pod<summary></summary>

```yaml
Image does not exist on docker
```

</details>

<details>What does the READY column in the output of the 'kubectl get pods' command indicate?<summary></summary>

```yaml
Running containers in a pod / Total containers in a pod
```

</details>

<details>Delete the 'webapp' Pod. Once deleted, wait for the pod to fully terminate.<summary></summary>

```yaml
kubectl delete pod webapp
```

</details>

<details>Create a new pod with the name 'redis' and with the image 'redis123'.<summary></summary>

```yaml
kubectl run redis --image=redis123 --generator=run-pod/v1 
```

</details>

<details>Create a new pod with the name 'redis' and with the image 'redis123'.<summary></summary>

```yaml
kubectl edit pod redis
```

</details>


