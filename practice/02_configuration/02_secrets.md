## ConfigMaps

<details><summary>How many secrets are there</summary>

```yaml
k get secrets 
```

</details>


<details><summary>Number of secrete defined in default-token secret</summary>

```yaml
k describe secrets default-token 
```

</details>


<details><summary>Type of secret</summary>

```yaml
k describe secrets default-token
# Look for type - service account - token
```

</details>


<details><summary>Create secret</summary>

```yaml
`kubectl create secret generic db-secret --from-literal=db-host=sql01 --from-literal=db-user=abc` 
```

</details>


<details><summary>Use recently created secrets in pod</summary>

```yaml
k get pod  web-aap -o yaml > pod.yaml 
k delete pod web-app
kubectl explain pods --recursive | less # serach for envFrom
#vi pod.yaml & add envFrom section
k apply -f pod.yaml
```

</details>