





### Docker
```bash
sudo apt-get update
sudo apt install docker.io -y
sudo usermod -aG docker $USER
sudo systemctl restart docker
```

### Minikube
```bash
# Install Docker
sudo su
sudo apt update && sudo apt -y install docker.io
sudo systemctl enable --now docker

# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl && sudo mv kubectl /usr/local/bin/

# Install Minikube
curl -Lo minikube https://github.com/kubernetes/minikube/releases/download/v1.24.0/minikube-linux-amd64
chmod +x minikube && sudo mv minikube /usr/local/bin/

# Start Minikube
sudo apt install conntrack -y
minikube start --vm-driver=none
minikube status
```
---

### Jenkins

```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
```
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---
### ArgoCD
- Install Argo CD using manifests
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

- Access the Argo CD UI (Loadbalancer service)
```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

- Get the Loadbalancer service IP
```bash
kubectl get svc argocd-server -n argocd
```

- Login to ArgoCD:
(The default username is admin and get the password using the following command):
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

---
### Sonarqube container
---
### Trivy container 
---



---
### Installing AWS CLI
```bash
#!/bin/bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip -y
unzip awscliv2.zip
sudo ./aws/install
```

---
### Installing Docker 
```bash
#!/bin/bash
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker jenkins
sudo usermod -aG docker ubuntu
sudo systemctl restart docker
sudo chmod 777 /var/run/docker.sock
```

---
### Installing Kubectl
```bash
#!/bin/bash
sudo apt update
sudo apt install curl -y
sudo curl -LO "https://dl.k8s.io/release/v1.28.4/bin/linux/amd64/kubectl"
sudo chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```
---

### Installing eksctl
```bash
#! /bin/bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```


---




Commit Date: 18-Aug-2025
