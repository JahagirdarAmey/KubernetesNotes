
## Deployements

<details><summary>How many Deployments exist on the system?</summary>

```yaml
kubectl get deployements
```

</details>

<details><summary>Why do you think the deployment is not ready?</summary>

```yaml
Image does not exists
kubectl describe deployements deployement_name | grep -i image
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
