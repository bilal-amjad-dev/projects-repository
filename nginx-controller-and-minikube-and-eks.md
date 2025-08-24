
### Ingress:
Ingress controller looks at Ingress and create Load Balancer.

### we have:
- dep.yaml
- svc.yaml
- ing.yaml




1. ### Enable Ingress Controller (for Minikube):

```bash
minikube addons enable ingress
```

2. ### Apply all Kubernetes Manifests
```bash
kubectl apply -f k8s/manifests/deployment.yaml
kubectl apply -f k8s/manifests/service.yaml
kubectl apply -f k8s/manifests/ingress.yaml
```


3. ### Get Ingress IP:
```bash
minikube ip
```

(This will give you the IP address, e.g., 192.168.49.2)



4. ### Modify Local Hosts File:

- Linux: `sudo vim /etc/hosts` 
- Windows: C:\Windows\System32\drivers\etc\hosts

Add this line, replacing <MINIKUBE_IP> with the IP from the previous step:
```bash
<MINIKUBE_IP>    go-web-app.local

(Example: 192.168.49.2    go-web-app.local)
```

Save the file.


**Access Your Application:**

Open your web browser and go to:

http://go-web-app.local



---
---
---

































Commit Date: 24-Aug-2025
