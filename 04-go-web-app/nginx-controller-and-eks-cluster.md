
We have:
- deployment.yaml
- service.yaml
- ingress.yaml


1. **Deploy Nginx Ingress Controller**

This command deploys the Nginx Ingress Controller to your EKS cluster. It will create a LoadBalancer Service for the controller itself, which AWS will fulfill with an Elastic Load Balancer (ELB).

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

2. **Verify Controller Installation (Wait for Pods to be Running):**

```bash
kubectl get pods --namespace ingress-nginx
kubectl get services --namespace ingress-nginx
```

Look for the `nginx-ingress-controller` service and note its `EXTERNAL-IP` (this will be an AWS ELB DNS name). It might take a few minutes for the ELB to provision.



3. **Apply Your Application's Kubernetes Manifests**
- Deploy your Go application, Service, and Ingress to the cluster.

```bash
kubectl apply -f k8s/manifests/deployment.yaml
kubectl apply -f k8s/manifests/service.yaml
kubectl apply -f k8s/manifests/ingress.yaml
```

4. **Get the External IP/Hostname for Access**
- Get the DNS name (hostname) of the Load Balancer provisioned by the Nginx Ingress Controller:
```bash
kubectl get svc -n ingress-nginx
```


5. **Edit the /etc/hosts File:**

```bash
sudo vim /etc/hosts
```

```bash
<ELB_IP_ADDRESS>    go-web-app.local
```


6. Access Your Application

Open your web browser and go to:
```bash
http://go-web-app.local
```







Commit Date: 19-Aug-2025
