ChatGPT said:
# 🛡️ Non-Root Execution for vLLM Docker Image

## 🎯 Purpose
This custom vLLM Docker image runs the server as a **non-root user** (`vllm`, UID/GID 1000).  
The goal is to improve **security**, **compliance**, and **Kubernetes compatibility** while keeping full functionality.

---

## 🔐 Why Non-Root?
Running containers as root is convenient but unsafe in production.  
Using a non-privileged user provides several benefits:

- **Improved security:** limits the impact of vulnerabilities and prevents privilege escalation.  
- **Best practices compliance:** aligns with Docker, CNCF, and Kubernetes security guidelines.  
- **Safer filesystem access:** avoids unintended writes or ownership issues.  

---

## ☸️ Why It Matters in Kubernetes
Kubernetes often enforces security policies (PSP, Pod Security Standards, Gatekeeper) that **block root containers by default**.  
Using a non-root user ensures the image:

- works with restricted PodSecurity profiles  
- mounts volumes safely with `runAsUser` / `fsGroup`  
- passes security scans and CI/CD checks  

---

## ✅ Summary
Running vLLM as a non-root user increases safety, aligns with modern cluster security standards, and makes the image production-ready for Kubernetes.
