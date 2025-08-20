# Go Web App — DevOps Example

A simple Go Web app containerized with Docker and deployed on Kubernetes. This repo shows how to do everything manually without automation. (In this, we are using ingress.)

---


## What is DevOps?

DevOps means combining development (Dev) and operations (Ops) to deliver code faster.

In this project, we do:
- Build Docker image
- Run container locally
- Push image to DockerHub
- Deploy app to Kubernetes

All steps are done manually to help beginners learn.

> **Important:** Remember you need to make these two changes in this project:
> 1. Replace `YOUR-DOCKERHUB-USERNAME` with your DockerHub username in the Docker tag and push commands.
> 2. Replace `YOUR-DOCKERHUB-USERNAME` with your DockerHub username in the `k8s/manifests/deployment.yaml` file under the `image` section.

---

## Prerequisites

- EC2 instance (t2.medium recommended)
- DockerHub account
- Docker installed
- Kubernetes installed (we will use Minikube here)
- kubectl installed (Kubernetes command line tool)

---

## Install Minikube and Dependencies

Run these commands to set up Minikube on Ubuntu:

```bash
# Switch to root user (optional)
sudo su

# Update packages and install Docker
sudo apt update && sudo apt -y install docker.io
sudo systemctl enable --now docker

# Install kubectl (Kubernetes CLI)
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube

# Install conntrack (required dependency)
sudo apt install -y conntrack

# Start Minikube (using none driver to run without VM)
minikube start --vm-driver=none

# Verify Minikube status
minikube status
```


## How to Use

### 1. Clone the Code

```bash
git clone https://github.com/bilal-amjad-dev/go-web-app.git
cd go-web-app
```



---

### 2. Docker: Build, Run, Push

**Build Docker Image:**


```bash
docker build -t go-web-app:v1 .
```



**Run Container Locally:**


```bash
docker run -it -p 8000:8000 go-web-app:v1
```




- Open port **8000** in your security group
- Open the app in browser: `http://<EC2_PUBLIC_IP>8000`

Press `CTRL+C` to stop.

**Push Image to DockerHub:**

Remember to replace `YOUR-DOCKERHUB-USERNAME` with your DockerHub username.


```bash
docker login
docker tag python-flask-app:v1 YOUR-DOCKERHUB-USERNAME/go-web-app:v1
docker push YOUR-DOCKERHUB-USERNAME/go-web-app:v1
```



---

### 3. Kubernetes: Deploy

Edit `k8s/manifests/deployment.yaml` file and replace:



```bash
image: YOUR-DOCKERHUB-USERNAME/go-web-app:v1
```



with your DockerHub username.

Deploy to Kubernetes:


```bash
kubectl apply -f k8s/manifests/deployment.yaml
kubectl apply -f k8s/manifests/service.yaml
kubectl apply -f k8s/manifests/ingress.yaml

```







There are 3 things we need to remember with respect to ingress:
- Ingress
- Ingress Controller
- Load Balancer


Ingress Controller will watch the Ingress and created Load Balancer.

We are telling Ingress Controller create a load balancer 

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.1/deploy/static/provider/aws/deploy.yaml
```

If i access the load balancer, not on the load balancer address but on this particular thing (go-web-app.local)
, it has to forward the request to this particular service. 
          service:
            name: go-web-app
            port:
              number: 80
			  
If the request is forwarded to the service, it will forward the request to the pods


I have done hundred of projects in my 10 years of experience 

```bash
kubectl get pods -n ingress-nginx 
kubectl get ing 
```

take lb ok

```bash
nslookup paste-your-load-balancer
```

you have got the IP Address 
Address: 3.231.186.46 

```bash
sudo vim /etc/hosts 
```

now:

3.231.186.46 paste-here-load-balancer


Escape:wq

The configuration will take time to reflect but once reflected you can see now the application is accessed on go-web-app.local 





---

### 4. Update the App

Make any change you want in `app.py` (e.g., change message).

Build, tag and push new version:



```bash
docker build -t go-web-app:v2 .
docker tag go-web-app:v2 YOUR-DOCKERHUB-USERNAME/go-web-app:v2
docker push YOUR-DOCKERHUB-USERNAME/go-web-app:v2
```




Change image version in `deployment.yaml` to `v2` and apply:


```bash
kubectl apply -f k8s/manifests/deployment.yaml
```



---

### 5. Clean Up

Remove deployment and service when done:



```bash
kubectl delete -f k8s/manifests/deployment.yaml
kubectl delete -f k8s/manifests/service.yaml
kubectl delete -f k8s/manifests/ingress.yaml
```



---

## Notes

- This project has manual DevOps steps for learning.
- Make sure to open proper ports in your firewall/security group.
- Replace `YOUR-DOCKERHUB-USERNAME` everywhere with your DockerHub account.
- For real projects, consider automating with CI/CD tools later.

---

Commit Date: 19-Aug-2025
Commit Date: 20-Aug-2025

