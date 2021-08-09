

### Pod Lifecycle

- Pending, 
- ContainerCreating
- Running


### Pod conditions 
- PodScheduled
- Initialized 
- ContainersReady
- Ready 


- To let k8s know that application is ready, different kind of tests
    - HTTP Test
    - TCP Test
    - Exes command 
    

```yaml
    readinessProbe:
      httpGet:
        path: /health
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
      failureThreshold : 8
```

###

```yaml
    readinessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
```

###Command

```yaml
    readinessProbe:
      exec:
        command: 
          - cat
          - /app/is_ready
```
