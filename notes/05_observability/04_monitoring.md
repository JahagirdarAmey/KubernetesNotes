# Monitoring 

Many solutions are available
- Metrics server
- Promotheus 
- Elastic Stack
- Data Dog
- Dynatrace 

Metrics server
- We can have one metrics server per k8s cluster
- In mem solution
- K8s runs an agent on each node Kubelet 
- Kubelet container sub-component cAdvisor

To start - git clone metrics server & k create -f 

kubectl top node 
kubectl top pod  
