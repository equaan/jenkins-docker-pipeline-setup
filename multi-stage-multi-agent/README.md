# Multi-Stage, Multi-Agent Jenkins Pipeline  
_Backend (Maven) + Frontend (Node.js)_

This project demonstrates how to build a **multi-stage CI/CD pipeline** where each stage uses a different Docker image and represents a different part of a 3-tier application.

Even though I did not implement a database stage yet, I built the pipeline in a way that resembles real-world CI/CD structure—frontend and backend running as separate stages, each inside their own clean Docker environment.

---

# 🎯 Why This Pipeline Was Created

The goal of this project was to understand:

- How to structure **multiple stages** in a Jenkins pipeline  
- How each stage can run using **different Docker images**  
- How Jenkins handles **ephemeral containers** for each stage  
- How pipelines can simulate **frontend and backend workflows**  
- How to run everything in one Jenkinsfile using `agent none`

This is a major step forward from a simple single-agent pipeline.

---

# 🧠 What I Wanted to Learn

### 1️⃣ Multi-stage pipeline structure
I wanted to understand how companies split CI flows:
- Backend build/validation
- Frontend build/validation

Even though this is a simple example (printing versions), the structure matches real CI flows.

---

### 2️⃣ How Docker images differ per stage
Backend uses:maven:3.8.1-adoptopenjdk-11
Frontend uses:node:16-alpine

This helped me understand:
- Why separate environments are important
- Why CI builds must be isolated
- How different tools require different containers

---

### 3️⃣ How Jenkins handles multiple agents/containers
Even though both stages ran on the same Ubuntu agent, each stage:

- spun up its own Docker container  
- executed its commands inside the container  
- stopped and removed the container afterward  

Meaning:
👉 **Zero leftover dependencies**  
👉 **No version conflicts**  
👉 **Fast, clean builds**

---

# ✔️ What actually happens during execution:
- **Jenkins pulls the repository**
- **Stage 1 → Starts a Maven container → prints version → removes container**
- **Stage 2 → Starts a Node container → prints version → removes container**

Each stage has its own environment. No overlap.

# 📌 What This Pipeline Taught Me
🔹 **How to build multi-stage Jenkins pipelines**

🔹 **How to use agent none with per-stage agents**

🔹 **How Docker images isolate build environments**

🔹 **How Jenkins dynamically pulls images when needed**

🔹 **How containers spin up and tear down automatically**

🔹 **Why companies structure CI exactly like this**
