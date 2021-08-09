# Security Context 

- In k8s, containers are encapsulated in pods, you may choose to configure security settings at container level or at pod level
- If you choose to configure at pod level, settings will carry over all the containers within pod
- If you choose to configure at both pod level & container level, settings on container will override , settings on pod 
