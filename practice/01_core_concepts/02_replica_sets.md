## ReplicaSets

<details><summary>How many ReplicaSets exist on the system?</summary>

```yaml
kubectl get replicaset OR kubectl get replicasets.apps
```

</details>

<details><summary>How many PODs are DESIRED in the new-replica-set?</summary>

```yaml
kubectl get replicaset OR kubectl get replicasets.apps
```

</details>

<details><summary>What is the image used to create the pods in the new-replica-set?</summary>

```yaml
kubectl describe replicasets.app name_of_replica_sets
```

</details>

<details><summary>How many PODs are READY in the new-replica-set?</summary>

```yaml
kubectl get replicaset # just like pods 
```

</details>

<details><summary>Why do you think the PODs are not ready?</summary>

```yaml
kubectl describe pod pod_name
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
Now, delete pods one by one, replicaSet will create new pods with specified image
```

</details>

<details><summary>Scale the ReplicaSet to 5 PODs</summary>

```yaml
kubectl scale replicaset --replicas=5 new-replica-set 
```

</details>

<details><summary>Now scale the ReplicaSet down to 2 PODs</summary>

```yaml
kubectl edit replicaset new-replica-set
```

</details>
