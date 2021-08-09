# VVIPM K8s Commands

## Pods

<details><summary>Creating pod by command</summary>

```yaml
kubectl run myapp-nginx --image=nginx
```
</details>


<details><summary>Creating pod definition file and applying it</summary>

```yaml
kubectl run myapp-nginx --image=nginx --dry-run=client -o yaml > pods.yaml # Does not create pod but creates definition file
kubectl apply -f pods.yaml
```
</details>


<details><summary>Edit existing pod</summary>

```yaml
kubectl edit pod redis
```

</details>

<details><summary>Create a busybox pod (using YAML) that runs the command "env"</summary>

```yaml
 kubectl run busybox --image=busybox --namespace=mynamespace --dry-run=client -o yaml --command -- env > busybox.yaml
# NOTE : --command --env is after -o yaml
```

</details>

<details><summary>Get the YAML for a new ResourceQuota called 'myrq' with hard limits of 1 CPU, 1G memory and 2 pods without creating it</summary>

```yaml
kubectl create quota myrq --hard=cpu=1,memory=1G,pods=2 --dry-run=client -o yaml
```

</details>

<details><summary>Create a pod with image nginx called nginx and expose traffic on port 80</summary>

```yaml
kubectl run nginx --image=nginx --restart=Never --port=80
```

</details>

<details><summary>Change pod's image to nginx:1.7.1.</summary>

```yaml
#kubectl set image POD/POD_NAME CONTAINER_NAME=IMAGE_NAME:TAG
kubectl set image pod/nginx nginx=nginx:1.7.1
```

</details>

<details><summary>Get pods yaml</summary>

```yaml
kubectl get po nginx -o yaml
```

</details>

<details><summary>Get pods description, information, investigation</summary>

```yaml
kubectl describe pod nginx
```

</details>

<details><summary>Pod logs</summary>

```yaml
kubectl logs nginx
kubectl logs nginx --previous # Logs for previous instance
```

</details>

<details><summary>Create an nginx pod and set an env value as 'var1=val1'</summary>

```yaml
kubectl --namespace=mynamespace run nginx --image=nginx --env=var1=val1
```

</details>

<details><summary>Display all env of pod</summary>

```yaml
kubectl --namespace=mynamespace exec -it nginx -- env
```

</details>

<details><summary>Create a busybox pod that echoes 'hello world' and then exits</summary>

```yaml
kubectl --namespace=mynamespace run buxybox --image=busybox  
```

</details>

## Namespaces

<details><summary>Create namespace</summary>

```yaml
kubectl create namespace mynamespace
```

</details>


<details><summary>Get yaml for namespace without creating it</summary>

```yaml
kubectl create namespace myns -o yaml --dry-run=client
```

</details>


