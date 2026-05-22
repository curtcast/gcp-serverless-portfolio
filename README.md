# ⚡ Serverless Full-Stack Portfolio Architecture on Google Cloud

![Deploy Status](https://github.com)

A highly available, decoupled, cloud-native microservices portfolio application hosted entirely on Google Cloud Platform (GCP). This project transitions a static HTML portfolio into a containerized modern web stack backed by automated integration and rolling deployments.

🌟 **[Live Project Demo Link](https://run.app)** 🌟

---

## 🏛️ System Architecture Diagram

```text
[ Client Browser ]
        │
        ├── (HTTP Requests / UI) ───────> [ portfolio-frontend ] 
        │                                 (Docker / Nginx Alpine on Cloud Run)
        │
        └── (Asynchronous API Fetch) ──> [ portfolio-backend ] 
                                          (Docker / Python Functions Framework on Cloud Run)
                                                  │
                                       (IAM Secure Auth)
                                                  ▼
                                         [ GCP Firestore NoSQL ]
```

---

## 🚀 Core Technical Features

* **📦 Dual Containerization**: Engineered an ultra-lightweight frontend service utilizing an **Nginx Alpine Linux** container environment to optimize resource efficiency.
* **⚡ Serverless Compute**: Deployed decoupled microservices independently on **Google Cloud Run**, allowing separate scaling, granular resource allocation, and \$0 idle execution cost.
* **🛠️ Cloud Native Backend**: Built an event-driven Python REST API using the **Google Functions Framework** to seamlessly handle request routing.
* **🗄️ Managed NoSQL Integration**: Integrated transactional atomicity inside **GCP Firestore** using native `firestore.Increment(1)` operations to mitigate database race conditions.
* **🔐 CI/CD Automation**: Designed an automated pipeline with **GitHub Actions** that securely authenticates via IAM, automates Docker builds, pushes layers to **Google Artifact Registry**, and triggers atomic rolling upgrades with zero downtime.
* **🛡️ Identity & Access Management (IAM)**: Applied the principle of least privilege, restricting container runtime execution to scoped Service Accounts and enforcing environment runtime parameter isolation.
* **💰 Budget Guardrails**: Implemented granular GCP budget configurations with automated alerting thresholds at 50%, 90%, and 100% actual-spend metrics to prevent runtime cost leakages.

---

## 📂 Project Structure

```text
gcp-serverless-portfolio/
├── .github/
│   └── workflows/
│       └── deploy.yml          # Automated multi-service CI/CD deployment logic
├── frontend/
│   ├── index.html              # Modular portfolio markup and JavaScript counter trigger
│   ├── nginx.conf              # Custom server mapping and strict anti-caching response headers
│   └── Dockerfile              # Production Nginx runtime compilation blueprint
├── backend/
│   ├── main.py                 # Core API transaction processing and Firestore initialization
│   ├── requirements.txt        # Managed Python environment dependencies
│   └── Dockerfile              # Cloud native Functions Framework runner orchestration
├── .dockerignore               # Local filesystem isolation directives
└── README.md                   # System documentation and deployment blueprints
```

---

## 🏃‍♂️ Local Development Setup

### Testing the Backend Image Locally
To simulate the serverless execution environment locally on your machine, navigate to the backend layer and build the image:

```bash
cd backend
docker build --no-cache -t local-backend .
docker run -p 8080:8080 local-backend
```
*(Note: A local run will safely throw a `DefaultCredentialsError` on code initialization if GCP client environment credentials are not present locally. This is resolved automatically when running in production on Cloud Run).*

