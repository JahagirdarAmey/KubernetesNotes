# Multi-Container Pod

  
- Shared same lifecycle
- Shared same network - refer to each other via localhost
- Shared same storage volume



    

- Two services needs to work together, Example :- web-server & log agent
- Services need to scale up & down together. 
- That's why multi-container pod 
    - Same network space, Can refer each other via localhost
    - 




Types

- Sidecar
    - Log agent & web-server example 
- Adapter
    - Suppose we have multiple apps sending logs in different format to log server, need to have adapter container which process logs before sending to log server 
- Ambassador
    - App may have different env
    - Rather than making changes to app, outsource thses to container, He will decide correct env props