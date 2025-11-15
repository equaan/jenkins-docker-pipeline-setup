# My First Jenkins Pipeline – Docker Agent Verification

This was the very first pipeline I created after setting up Jenkins and Docker on my EC2 instance.

The main goal was simple:
👉 **Check if Jenkins can successfully run a pipeline inside a Docker container.**

But this small test taught me a LOT about how Jenkins actually works.

---

# 🎯 What I Wanted to Understand
Before writing the pipeline, I wanted to verify 3 key concepts:

### 1️⃣ Can Jenkins talk to Docker?
By default, only the `root` user can access the Docker daemon.  
So I had to:
- switch to root  
- add `jenkins` and `ubuntu` users to the `docker` group  
- restart Docker  
- restart Jenkins  

Only after that Jenkins could run commands like: docker run hello-world


### 2️⃣ How does Jenkins use Docker as an agent?
I used the simple Jenkinsfile which:
-pull node:16-alpine (if not present)
-create a temporary container
-execute the command
-delete the container afterwards

### 3️⃣ Does Jenkins actually create and destroy containers automatically?
When I ran the pipeline, the logs told the full story:
-Jenkins first checked if node:16-alpine exists → it didn’t
-Jenkins pulled it from Docker Hub
-Jenkins created a short-lived container
-Ran node --version inside that container
-Stopped and removed the container immediately

This was the most important learning:
👉 **No container stays alive unless a build is happening.**

This solves:
-cost issues
-scaling problems
-dependency conflicts

# ✔️ What I Learned From This Pipeline
🔹 **Jenkins Master does NOT run builds:**
It only schedules & orchestrates.
The actual build happens inside the Docker container.

🔹 **Docker-based agents = Zero idle cost:**
VM agents always stay ON.
Docker agents exist only during the pipeline.

🔹 **Pipeline-as-Code (Jenkinsfile) is superior to Freestyle:**
Everything is versioned in GitHub.

🔹 **Clean, reproducible environments:**
Every build starts fresh — no leftover dependencies.
