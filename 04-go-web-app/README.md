

Ingress:

we have:
- dep
- svc
- ing


- **Enable Ingress Controller (for Minikube):**

```bash
minikube addons enable ingress
```

3. **Apply all Kubernetes Manifests:**
```bash
kubectl apply -f k8s/manifests/deployment.yaml
kubectl apply -f k8s/manifests/service.yaml
kubectl apply -f k8s/manifests/ingress.yaml
```


4. **Get Ingress IP:**
```bash
minikube ip
```
(This will give you the IP address, e.g., 192.168.49.2)



5. **Modify Local Hosts File:**
Linux: `sudo vim /etc/hosts` 
Windows: C:\Windows\System32\drivers\etc\hosts
Add this line, replacing <MINIKUBE_IP> with the IP from the previous step:

```bash
<MINIKUBE_IP>    go-web-app.local
```
(Example: 192.168.49.2    go-web-app.local)

Save the file.


6. **Access Your Application:**

Open your web browser and go to:
```bash
http://go-web-app.local
```





















Commit Date: 19-Aug-2025
