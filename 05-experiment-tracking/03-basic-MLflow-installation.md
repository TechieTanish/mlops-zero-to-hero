# 🚀 Production-Grade MLflow Setup on Kubernetes (Stateful Architecture)

This README explains **how to deploy MLflow in a real production environment** using **Kubernetes**, **AWS RDS (PostgreSQL)**, and **cloud-native best practices**. It also clarifies **why a stateless MLflow setup fails** and how to design a **stateful architecture without breaking Kubernetes principles**.

---

## 📌 Why This Matters

Many beginners deploy MLflow directly on Kubernetes using local storage. This works in demos, but **fails in production** due to **data loss**.

### ❌ Problem With Stateless MLflow

* Kubernetes pods are **ephemeral**
* Pod restart = **MLflow data wiped**
* New MLflow instance = **old experiments gone**

This happens because MLflow stores:

* Experiments
* Runs
* Metrics
* Parameters

If this state is stored **inside the pod**, Kubernetes will eventually delete it.

👉 **Conclusion:** MLflow must use a **stateful backend** in production.

---

## ✅ Correct Production Architecture

MLflow itself stays **stateless**, but all **state is externalized**.

```
User
  ↓
LoadBalancer / Ingress
  ↓
MLflow Tracking Server (K8s - Stateless)
  ↓
Backend Store → PostgreSQL (AWS RDS)
  ↓
Artifact Store → S3 Bucket
```

### 🔑 Key Principle

> Kubernetes handles compute.
> Managed cloud services handle state.

---

## 🧱 Components Overview

### 1️⃣ MLflow Tracking Server

* Runs as a **Kubernetes Deployment**
* Can be restarted or scaled safely
* No local persistent storage

### 2️⃣ PostgreSQL (AWS RDS)

Stores:

* Experiment metadata
* Run parameters
* Metrics

Benefits:

* Automated backups
* High availability
* Persistence independent of K8s

### 3️⃣ Artifact Store (S3)

Stores:

* Models
* Logs
* Artifacts

Why S3:

* Durable
* Scalable
* Cost-effective

---

## 🛠️ Step-by-Step Production Setup

---

### 🔹 Step 1: Setup AWS RDS (PostgreSQL)

* Create PostgreSQL RDS instance
* Enable public access (or private via VPC peering)
* Allow inbound traffic from Kubernetes nodes
* Note the following:

  * DB endpoint
  * Port: `5432`
  * Username & password

---

### 🔹 Step 2: Create MLflow Database

In PostgreSQL:

* Create a database (example: `mlflow_db`)
* Create a dedicated MLflow user
* Grant required permissions

This improves:

* Security
* Isolation
* Production safety

---

### 🔹 Step 3: Configure MLflow Backend Store

MLflow uses PostgreSQL as the **backend store**:

```
postgresql://<user>:<password>@<rds-endpoint>:5432/mlflow_db
```

This ensures:

* Experiments survive pod restarts
* No metadata loss

---

### 🔹 Step 4: Configure Artifact Store (S3)

Set default artifact location:

```
s3://<mlflow-artifacts-bucket>
```

Without this:

* Artifacts go to local disk
* Silent data loss occurs later

---

### 🔹 Step 5: Deploy MLflow on Kubernetes

Recommended setup:

* **Deployment** (not StatefulSet)
* Stateless containers
* Horizontal scaling supported

Include:

* Kubernetes Service
* Ingress or LoadBalancer

MLflow server flags:

* `--backend-store-uri`
* `--default-artifact-root`

---

## 🌐 VPC Explained (Important)

### What is a VPC?

A **VPC (Virtual Private Cloud)** is a **private network**, not a limit on instances.

AWS default VPC provides:

* Subnets
* Routing tables
* Internet Gateway

You can run:

* EKS (Kubernetes)
* EC2
* RDS

Inside the **same VPC** securely.

---

### Why VPC is Critical for MLflow

* Secure communication between:

  * MLflow (K8s)
  * PostgreSQL (RDS)
* Control public vs private access
* Production-grade network isolation

---

## 🔐 Security Best Practices

* Use IAM roles for S3 access
* Restrict RDS security groups
* Avoid hardcoding secrets
* Use Kubernetes Secrets

---

## 🧠 Core Production Insight

> MLflow should remain stateless.
> The **state must live in managed services**.

This is **cloud-native design**, not a workaround.

---

## 🎯 What You Learned (MLOps Thinking)

* Why stateless services exist
* Why persistence must be external
* How Kubernetes handles failures
* Difference between demo and production

This is **real MLOps**, not tutorial-level deployment.

---

## 📌 Summary

| Component        | Role              |
| ---------------- | ----------------- |
| MLflow Server    | Stateless compute |
| PostgreSQL (RDS) | Metadata store    |
| S3               | Artifact storage  |
| Kubernetes       | Orchestration     |
| VPC              | Secure networking |

---

## ✅ Ready for Production

With this architecture:

* Pod restarts are safe
* Data is persistent
* System is scalable
* Cloud-native best practices are followed

---

**Author:** Tanish
**Focus:** MLOps • Kubernetes • Production Systems
**Formated or organize by @ChatGPT**