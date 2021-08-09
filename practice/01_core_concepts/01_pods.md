## Pods

<details><summary>How many PODs exist on the system? in the current(default) namespace</summary>

```yaml
kubectl get pods
```

</details>

<details><summary>Create a new pod with the NGINX image</summary>

```yaml
kubectl run myapp-nginx --image=nginx
```
- Deploys docker container by creating a pod
</details>

<details><summary>What is the image used to create the new pods?</summary>

```yaml
kubectl describe pods | grep image
```

</details>

<details><summary>Which nodes are these pods placed on?</summary>

```yaml
kubectl describe pods | grep Node:
  or
kubectl describe pods -o wide
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
kubectl run redis --image=redis123 --dry-run=client -o yaml > pods.yaml # Does not create but creates defination file
kubectl apply -f pods.yaml
```

</details>

<details><summary>Create a new pod with the name 'redis' and with the image 'redis123'.</summary>

```yaml
kubectl edit pod redis
```

</details>
