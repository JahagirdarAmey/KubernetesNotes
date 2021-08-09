
##Namespaces

<details><summary>How many Namespaces exist on the system?</summary>

```yaml
kubectl get namespaces --no-headers | wc -l
```

</details>

<details><summary>How many pods exist in the 'research' namespace?</summary>

```yaml
kubectl get pods --namespace=research --no-headers 
```

</details>

<details><summary>Create a POD in the 'finance' namespace.</summary>

```yaml
kubectl run redis --image=redis --dry-run=client -o yaml > pod.yml and then add namespace in pod.yaml & kubectl apply 
kubectl run redis --image=redis --generator=run-pod/v1 --namespace=finance 
```

</details>

<details><summary>Which namespace has the 'blue' pod in it?</summary>

```yaml
kubectl get pods --all-namespaces | grep blue
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
kubectl --namespace=dev get svc 


db-service.dev.svc.cluster.local
```

</details>
