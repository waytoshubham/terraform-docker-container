# 🐳 Terraform Docker Container Provisioning

This project demonstrates the use of **Infrastructure as Code (IaC)** with **Terraform** to provision a **local Docker container** running the **Nginx web server**. It walks through the full lifecycle of container provisioning — including creation, inspection, and destruction — entirely through Terraform.

---

## 📌 Objective

Provision a Docker container locally using Terraform to understand the principles of Infrastructure as Code.

---

## 🛠️ Tools & Technologies

- **Terraform** – IaC tool to provision infrastructure
- **Docker** – Container runtime for local container management
- **Nginx** – Web server used as the containerized application
- **Windows OS** – Local setup environment

---

---

## ⚙️ Terraform Configuration (`main.tf`)

The configuration does the following:

1. Uses the Docker provider to connect to the local Docker engine.
2. Pulls the latest `nginx` Docker image.
3. Runs a container exposing **port 80** of the container to **port 8080** on the host.

```hcl
provider "docker" {
  host = "npipe:////./pipe/docker_engine"
}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  name  = "nginx_container"
  image = docker_image.nginx.name

  ports {
    internal = 80
    external = 8080
  }
}
---

---
## 🚀 How to Run the Project

🔧 Prerequisites

Docker Desktop installed and running

Terraform installed

PowerShell or Command Prompt (run as Administrator if needed)

✅ Steps to Provision
1. Initialize the project
    terraform init

2. Preview the execution plan
    terraform plan

3. Apply the configuration
    terraform apply

👉 Type yes when prompted.

4. Verify the container is running
    docker ps

5. Visit Nginx in browser
    http://localhost:8080

---
---
## 🧹To Destroy the Infrastructure
    terraform destroy

👉 Confirm with yes when prompted.
---

---
## 🔍 Useful Terraform Commands

    **terraform init** — Initializes Terraform project and downloads provider plugins

    **terraform plan** — Shows what Terraform will do

    **terraform apply** — Applies the changes and provisions infrastructure

    **terraform destroy** — Tears down the created infrastructure

    **terraform state list** — Lists all tracked resources

    **terraform show** — Shows details of the Terraform state
---
```
