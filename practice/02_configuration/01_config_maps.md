## ConfigMaps

<details><summary>What is the environment variable name set on the container in the pod?</summary>

```yaml
kubectl describe pod webapp-color 
```

</details>

<details><summary>Update the environment variable on the POD to display a green background. Note: Delete and recreate the POD. Only make the necessary changes. Do not modify the name of the Pod.</summary>

```yaml
kubectl get pod webapp-color -o yaml > pod.yaml
kubectl delete pod webapp-color 
kubectl apply -f pod.yaml
```

</details>
<details><summary>How many ConfigMaps exist in the environment?</summary>

```yaml
kubectl get configmaps
```

</details>
<details><summary>Identify the database host from the config map db-config</summary>

```yaml
kubectl describe cm db-config
```

</details>
<details><summary>Create a new ConfigMap for the webapp-color POD. Use the spec given below.</summary>

```yaml
kubectl create cm webapp-config-map --from-literal=APP_COLOR=darkblue
```

</details>
<details><summary>Update the environment variable on the POD to use the newly created ConfigMap


Note: Delete and recreate the POD. Only make the necessary changes. Do not modify the name of the Pod.</summary>

```yaml
kubectl delete pod webapp-color
kubectl explain pods --recursive | grep envFrom -A3
# Replace envFrom with env
kubectl apply -f pod.yml
```
</details>