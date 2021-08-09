# Liveness Probe

- To check if application is actually healthy 
- Kubernetes uses liveness probes to know when to restart a container. If a container is unresponsive—perhaps the application is deadlocked due to a multi-threading defect—restarting the container can make the application more available, despite the defect.


```yaml
    livenessProbe:
      httpGet:
        path: /health
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
      failureThreshold : 8
```

###

```yaml
    livenessProbe:
      tcpSocket:
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
```

###Command

```yaml
    livenessProbe:
      exec:
        command: 
          - cat
          - /app/is_ready
```
