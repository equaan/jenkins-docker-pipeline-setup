# jenkins-docker-pipeline-setup

This repository contains all the Jenkins pipeline projects I implemented while learning CI/CD with Docker-based agents and multi-node Jenkins architecture.

The goal was not just to follow steps, but to understand:
- Why Jenkins uses agents
- Why Docker-based agents solve scaling & cost issues
- How multi-stage pipelines are designed
- How real companies separate workloads across different OS nodes
- How to write clean, version-controlled pipelines using Jenkinsfile

---

## 📁 Projects in This Repository

### 🔹 **1. my-first-pipeline/**
My first Jenkins pipeline using Docker as an agent.  
It verifies whether Jenkins can:
- talk to Docker  
- spin up containers dynamically  
- run commands inside containers  
- teardown containers after use  

This pipeline is the foundation for everything else.

➡️ Includes Jenkinsfile + detailed README of my understanding.

---

### 🔹 **2. multi-stage-multi-agent/**
A multi-stage CI/CD pipeline that simulates a real 3-tier application:
- **Backend CI** → Maven build (runs inside Docker on Ubuntu node)
- **Frontend CI** → Node.js (runs inside Docker on Ubuntu node)
- **Database CI** → DB validation (runs on CentOS node)

This helped me understand:
- agent none  
- per-stage agents  
- running different stages on different OS machines  
- ephemeral containers inside agents  

➡️ Includes Jenkinsfile + deep explanation of my thought process.

---

## 🧰 Tools & Technologies I Used

- Jenkins (LTS)
- Docker
- AWS EC2 (Ubuntu + CentOS)
- Maven
- Node.js
- GitHub SCM integration
- Pipeline-as-Code (Jenkinsfile)

---

## 🎯 What I Learned

- How Jenkins master & agents work  
- Why companies prefer Docker-based agents for scalability  
- How to build CI/CD pipelines using Jenkinsfile  
- How to route stages to different Jenkins nodes  
- Real-world CI/CD architecture patterns  

This repo is a clean documentation of my hands-on learning and practical implementation.

