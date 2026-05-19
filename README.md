# 🚀 Building and Managing Container Images with Docker, Harbor & Kubernetes

This project demonstrates the complete lifecycle of building, optimizing, securing, storing, and deploying containerized applications using Docker, Harbor Private Registry, and Kubernetes.

## 📌 Project Overview

In this lab, I built and managed container images from scratch, implemented Docker best practices, configured a private registry using Harbor, and deployed the application to Kubernetes with secure private image pulling.

This project covers:

- Docker image creation
- Multi-stage builds for optimization
- Private container registry setup with Harbor
- Kubernetes image pull authentication
- Application deployment in Kubernetes
- Container security best practices
- Monitoring and update strategies

---

## 🛠️ Tech Stack

- **Docker**
- **Dockerfile**
- **Nginx**
- **Node.js**
- **Harbor Private Registry**
- **Kubernetes**
- **Minikube**
- **kubectl**
- **Linux (Ubuntu 20.04)**

---

## 📂 Project Structure

```bash
container-lab/
├── webapp/
│   ├── Dockerfile
│   ├── Dockerfile.multistage
│   ├── index.html
│   ├── nginx.conf
│   ├── package.json
│   ├── build.js
│   ├── public/
│   │   ├── index.html
│   │   └── app.js
│   └── dist/
├── webapp-deployment.yaml
├── update-app.sh
└── README.md
```

---

## 🔥 Key Features

### 1. Docker Image Creation
- Built a basic Docker image for an Nginx web app
- Created custom Dockerfiles
- Tagged and versioned images properly

### 2. Multi-Stage Builds
Optimized container images by:

- Separating build and production stages
- Removing unnecessary dependencies
- Reducing final image size
- Improving security posture

### 3. Private Registry with Harbor
Configured Harbor as a private registry:

- Created private projects
- Authenticated Docker with Harbor
- Pushed versioned images securely

### 4. Kubernetes Deployment
Deployed the application to Kubernetes with:

- Deployment
- Service
- Ingress
- Resource limits
- Health checks

### 5. Security Best Practices
Implemented:

- Non-root containers
- Health checks
- Private registry authentication
- Image vulnerability scanning

### 6. Monitoring & Updates
Created scripts for:

- Rolling application updates
- Monitoring pod resources
- Deployment rollout tracking

---

## ⚙️ Build & Run

### Build Basic Image

```bash
docker build -t webapp-basic:v1.0 .
```

### Build Optimized Multi-Stage Image

```bash
docker build -t webapp-optimized:v1.0 -f Dockerfile.multistage .
```

### Run Container

```bash
docker run -d -p 8080:80 webapp-optimized:v1.0
```

---

## 📦 Push to Harbor Registry

```bash
docker login localhost
docker tag webapp-optimized:v1.0 localhost/container-lab/webapp:v1.0
docker push localhost/container-lab/webapp:v1.0
```

---

## ☸️ Deploy to Kubernetes

```bash
kubectl apply -f webapp-deployment.yaml
```

Check deployment:

```bash
kubectl get pods -n container-lab
kubectl get svc -n container-lab
```

---

## 🔐 Kubernetes Private Registry Secret

```bash
kubectl create secret docker-registry harbor-secret \
  --docker-server=localhost \
  --docker-username=admin \
  --docker-password=<password> \
  -n container-lab
```

---

## 📊 Monitoring

Monitor resources:

```bash
kubectl top pods -n container-lab
```

Watch deployments:

```bash
kubectl rollout status deployment/webapp-deployment -n container-lab
```

---

## 📈 Learning Outcomes

Through this project, I learned:

- Containerization fundamentals
- Docker image optimization
- Private registry management
- Kubernetes image pull secrets
- Production-grade deployments
- Security hardening for containers

---

## 🎯 Real-World Relevance

This project is highly relevant for:

- DevOps Engineers
- Kubernetes Administrators
- Cloud Engineers
- Platform Engineers
- CKAD/CKA Preparation

---

## 👨‍💻 Author

**Zohaib Ahmed**  
DevOps Engineer | Kubernetes | Docker | Linux | AI/ML Enthusiast
