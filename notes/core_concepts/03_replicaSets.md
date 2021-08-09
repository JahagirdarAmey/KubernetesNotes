# ReplicaSets
- Replication controller 
- It is one of the k8s controller  (Architectural component)
- Replication controller helps us to run multiple instances of a single pod in k8s cluster which provides us high availibility 
- Replication controller also can work with Single pod
- Replication controller ensures specified number of pods are running all time
- Also used for load balancing 
- ReplicaSets can span across nodes - L21|2.17
- ReplicaSet is new & replication conroller is old
```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: nginx
spec:
  replicas: 3
  selector:
    app: nginx
  template:
    metadata:
      name: nginx
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```
- `template` is complete pod definition file except apiVerion & kind
- Note replicas are 3
-` k get replicationcontroller`
  
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  # modify replicas according to your case
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```

- ReplicaSets require selector definition (Major difference)
- `k get replicaset`

### To scale replicaSets 
1. Update replicas and run `k replace -f file.yaml`
2. `k scale --replicas=6 -f file.yaml`  OR `k scale --replicas=6 -f replicaName`
Please note even if you scale replicas using file, File will still contain replicas as 6
   
Also, There are options available to auto-scale depending on load. 


### Comman Commands 

```
k create -f file.yml
k get replicaset
k delete replicaset replicaset-name
k replace -f replicaset file.yml
k scale --replicas=6 -f file.yml
```
