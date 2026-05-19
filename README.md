# Serverless Full-Stack Portfolio Architecture on Google Cloud

A highly available, full-stack serverless portfolio application hosted entirely on Google Cloud Platform (GCP). This project transitions a static HTML frontend resume into a dynamic enterprise web stack by implementing custom serverless microservices and managed NoSQL database integrations.

👉 **[Live Project Demo Link](https://googleapis.com)**

## 🛠️ System Architecture Diagram

```text
[Frontend Browser] ➔ [GCP Cloud Storage Website Bucket]
                          │ (JavaScript API Fetch Call)
                          ▼
               [GCP Cloud Run Functions]
                          │ (Secure IAM Service Account Authentication)
                          ▼
                 [GCP Firestore NoSQL]
```

## ⚡ Core Technical Features

* **Serverless Compute**: Built a decoupled backend microservice using **Cloud Run Functions** (Python 3.11) configured with strict runtime environment parameters.
* **NoSQL Integration**: Integrated transactional atomicity inside **Firestore** using native `firestore.Increment(1)` logic to safely log incoming web visits without race conditions.
* **Secure Permissions**: Implemented strict principle of least privilege using granular **IAM Service Account** roles for database mutations rather than open public tokens.
* **Static Content Hosting**: Leveraged **Google Cloud Storage (GCS)** configured for public web asset delivery and main homepage index mapping suffix redirection.

## 📂 Project Structure

```text
gcp-serverless-portfolio/
├── frontend/
│   └── index.html         # Managed styled frontend portfolio markup
├── backend/
│   ├── main.py            # Python microservice transaction backend engine
│   └── requirements.txt   # Runtime project dependencies
├── .gitignore             # Environment artifact tracking safety rules
└── README.md              # Technical project documentation blueprint
```

## 🚀 How to Run Locally (Testing the API Connection)
1. Clone the repository down into your environment.
2. Navigate into the `/backend` layer and deploy to your GCP project console layout using the official Google Cloud SDK engine.
3. Replace the frontend JavaScript variables inside `index.html` with your custom live trigger endpoint URL.
