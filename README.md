# 🧮 Calculator Microservice – Cloud Deployment (SIT737 2025 - Prac 5.2D)

This microservice performs basic arithmetic operations and is:
- Built with **Node.js + Express**
- Dockerized and tagged as `calculator-microservice:latest`
- Stored in **Google Artifact Registry**
- Pulled and run locally from the cloud ✅

---

## 📦 Microservice Features

| Endpoint         | Example                       | Output        |
|------------------|-------------------------------|---------------|
| `/add`           | `/add?a=5&b=6`                | `{"result":11}` |
| `/divide`        | `/divide?a=4&b=2`             | `{"result":2}`  |
| *More routes available in app.js* |

---

## 🚀 Deployment Summary

### ✅ 1. Authenticate with Google Cloud
```bash
gcloud auth login
gcloud config set project sit737-25t1-shibu-9079054

✅ 2. Configure Docker for Google Artifact Registry
gcloud auth configure-docker australia-southeast2-docker.pkg.dev

✅ 3. Tag the Docker Image
docker tag calculator-microservice australia-southeast2-docker.pkg.dev/sit737-25t1-shibu-9079054/calculator-microservices/calculator-microservice:latest

✅ 4. Push the Image to Artifact Registry
docker push australia-southeast2-docker.pkg.dev/sit737-25t1-shibu-9079054/calculator-microservices/calculator-microservice:latest

✅ 5. Pull the Image from Cloud (Test from Artifact Registry)
docker pull australia-southeast2-docker.pkg.dev/sit737-25t1-shibu-9079054/calculator-microservices/calculator-microservice:latest

✔️ Output:
Status: Image is up to date for australia-southeast2-docker.pkg.dev/...

✅ 6. Run the Microservice Locally (From Cloud Image)
docker run -p 3003:2002 australia-southeast2-docker.pkg.dev/sit737-25t1-shibu-9079054/calculator-microservices/calculator-microservice:latest

✔️ Output:
Calculator microservice running on http://localhost:2002
info: Server started on port 2002 {"service":"calculator-microservice"}
info: Add: 5 + 6 = 11 {"service":"calculator-microservice"}
info: Divide: 4 / 2 = 2 {"service":"calculator-microservice"}

🌐 Test in Browser 
http://localhost:2002/add?a=5&b=6
http://localhost:2002/divide?a=4&b=2
