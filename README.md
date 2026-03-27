# Hosting-with-Ngrok

# 🚀 Local Dev Ingress System (Docker + Nginx + ngrok)

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Containerized-blue?logo=docker" />
  <img src="https://img.shields.io/badge/Nginx-Reverse%20Proxy-green?logo=nginx" />
  <img src="https://img.shields.io/badge/ngrok-Static%20Domain-black" />
  <img src="https://img.shields.io/badge/Status-Working-success" />
</p>

---

## 🌍 Overview

Built a **production-style ingress system locally** using:

* 🐳 Docker
* 🌐 Nginx (Reverse Proxy)
* 🔗 ngrok (Free Plan with Static Domain)

👉 Goal:
Expose **multiple local services** using **only ONE ngrok tunnel**.

---

## 🧠 Problem Statement

ngrok free plan allows:

> ❌ Only ONE active tunnel
> ❌ Cannot expose multiple ports simultaneously

---

## 💡 Solution

Designed a **reverse proxy architecture**:

```
Internet (ngrok static domain)
        ↓
Nginx Reverse Proxy (8080)
        ↓
 ┌───────────────┬───────────────┬───────────────┐
 ↓               ↓               ↓
Frontend       FastAPI        File Server
(3000)         (8000)         (6060)
```

---

## 🛠️ Tech Stack

* Docker & Docker Compose
* Nginx
* ngrok
* FastAPI
* Python HTTP Server

---

## ⚙️ Key Features

✔ Single ngrok tunnel (free-plan compliant)
✔ Static domain (no more changing URLs)
✔ Multi-service routing via Nginx
✔ Dockerized infrastructure
✔ Clean and scalable architecture

---

## 📁 Project Structure

```
.
├── docker-compose.yml
├── nginx.conf
├── ngrok-dev.yml
├── .env
└── README.md
```

---

## 🔥 Challenges Faced & Fixes

### 1️⃣ ngrok Free Plan Limitation

**Issue:** Only one tunnel allowed
**Fix:** Used Nginx reverse proxy to route multiple services

---

### 2️⃣ Static Domain Not Working

**Issue:** `endpoint offline`
**Cause:** Wrong ngrok account (token mismatch)
**Fix:** Used correct authtoken + isolated config

---

### 3️⃣ Config Not Being Used

**Issue:** Global config overriding local
**Fix:** Mounted config via Docker volume

---

### 4️⃣ No Logs from ngrok

**Issue:** Container running but silent
**Fix:** Corrected `command` in docker-compose

---

### 5️⃣ Frontend White Screen

**Issue:** JS files 404 under `/site`
**Fix:** Served frontend at `/`

---

### 6️⃣ ERR_NGROK_8012 (Critical)

**Issue:**

```
undefined://undefined
```

**Cause:** Missing protocol in upstream

**Fix:**

```yaml
addr: http://host.docker.internal:8080
```

---

### 7️⃣ Docker Networking Issue

**Issue:** Container couldn’t access host
**Fix:** Used:

```
host.docker.internal
```

---

## 🚀 Final Result

🌍 Static URL working
🔀 Multi-service routing
🐳 Fully containerized
⚡ Production-like setup

---

## 📸 Preview

* `/` → Frontend
* `/api` → FastAPI
* `/files` → Python server

---

## 🧠 Key Learnings

* Reverse proxy design (real-world concept)
* Docker networking fundamentals
* ngrok limitations & workarounds
* Config isolation & debugging
* Infrastructure-first thinking

---

## 🔮 Future Improvements

* 🔐 Add authentication (Nginx)
* 🌍 Deploy on VPS (24/7 uptime)
* 📦 Dockerize all services
* 🤖 Integrate with n8n workflows
* ⚡ Auto-start services on boot

---

## 👨‍💻 Author

**Khushal Sainiwal (KK-05)**
🎓 B.Tech CSE | 💻 Web Dev | 🤖 AI/ML Enthusiast

---

<p align="center">
  ⭐ If you found this useful, consider starring the repo!
</p>
