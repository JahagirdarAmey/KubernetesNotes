# Recap Core Concepts 

## Imperative Commands 


<details><summary>Deploy a pod named nginx-pod using the nginx:alpine image.</summary>

```yaml
kubectl run --generator=run-pod/v1 nginx-pod --image=nginx:alpine
```

</details>

<details><summary>Deploy a redis pod using the redis:alpine image with the labels set to tier=db.</summary>

```yaml
kubectl run --generator=run-pod/v1 redis --image=redis:alpine -l tier=db
```

</details>

<details><summary>Create a service redis-service to expose the redis application within the cluster on port 6379</summary>

```yaml
kubectl expose pod redis --port=6379 --name redis-service

TODO How
```

</details>

<details><summary>Create a deployment named webapp using the image kodekloud/webapp-color with 3 replicas</summary>

```yaml
kubectl create deployment webapp --image=kodekloud/webapp-color
kubectl scale deployment/webapp --replicas=3
TODO How
```

</details>

<details><summary>Expose the webapp as service webapp-service application on port 30082 on the nodes on the cluster</summary>

```yaml
kubectl expose pod redis --port=30082 --name webapp-service
```

</details>


[Commands and arguments]https://kodekloud.com/courses/kubernetes-certification-course-labs/lectures/12039454

<details><summary>What is the command used to run the pod 'ubuntu-sleeper'?</summary>

```yaml
kubectl describe pod
```

</details>

<details><summary>Create a pod with the ubuntu image to run a container to sleep for 5000 seconds. Modify the file ubuntu-sleeper-2.yaml.
Note: Only make the necessary changes. Do not modify the name.</summary>

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: ubuntu-sleeper-2
spec:
  containers:
  - name: ubuntu
    image: ubuntu
    command:
      - "sleep"
      - "1200"
```

</details>

<details><summary>Create a pod with the ubuntu image to run a container to sleep for 5000 seconds. Modify the file ubuntu-sleeper-2.yaml.
Note: Only make the necessary changes. Do not modify the name.</summary>

```yaml
Both sleep and 1200 should be defined as a string.
```

</details>

<details><summary>Update pod 'ubuntu-sleeper-3' to sleep for 2000 seconds.
Note: Only make the necessary changes. Do not modify the name of the pod. Delete and recreate the pod if necessary.</summary>

```yaml
Edit yaml
Delete pod
create pod 
```

</details>

<details><summary>Inspect the file 'Dockerfile' given at /root/webapp-color. What command is run at container startup?</summary>

```yaml
py app.py --color red 
```

</details>

<details><summary>Inspect the two files under directory 'webapp-color-2'. What command is run at container startup?
Assume the image was created from the Dockerfile in this folder</summary>

```yaml
kubernetes file overrides the dockerfile
```

</details>
<details><summary>Inspect the two files under directory 'webapp-color-3'. What command is run at container startup?
Assume the image was created from the Dockerfile in this folder</summary>

```yaml
#TODO Command in spec: needs to be clear
```

</details>


[ConfigMaps]https://2886795271-30099-kitek06j.environments.katacoda.com/#!/view1

<details><summary>What is the environment variable name set on the container in the pod?</summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

<details><summary></summary>

```yaml

```

</details>

