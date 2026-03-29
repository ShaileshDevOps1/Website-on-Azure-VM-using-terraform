# Website-on-Azure-VM-using-terraform
Azure VM Nginx Website Hosting (Terraform Project)
Here’s a **complete, step-by-step `README.md`** you can directly use to **publish your Terraform + Nginx VM project on GitHub** 🚀

---

# 🌐 Azure VM Nginx Website Hosting (Terraform Project)

## 📌 Project Overview

This project demonstrates how to:

* Provision an Azure Virtual Machine using **Terraform**
* Install and configure **Nginx**
* Deploy a **static website (multi-file)**
* Access the website via **public IP on port 80**

---

## 🧠 Architecture

```text
User Browser → Public IP → Port 80 → Nginx → Website Files
```

---

## 🛠️ Tech Stack

* Terraform
* Microsoft Azure
* Linux VM (Ubuntu)
* Nginx
* SSH
* PowerShell / Bash

---

# 🏗️  Deploy Infrastructure

## Initialize Terraform

```bash
terraform init
```

---

## Validate Code

```bash
terraform validate
```

---

## Plan Deployment

```bash
terraform plan
```

---

## Apply Configuration

```bash
terraform apply
```

Type:

```bash
yes
```

---

## Get Public IP

```bash
terraform output
```

---


# 🔐 Connect to VM

```powershell update based on your key location
ssh -i "C:\path\VMdemo_key.pem" azureuser@<public-ip>
```

---
If Key Does NOT Exist (Create One)

If .ssh folder is empty:

Create SSH key:
~~~
ssh-keygen -t rsa -b 4096
~~~

Press Enter for defaults.

👉 It will create:

C:\Users\Shailesh\.ssh\id_rsa
C:\Users\Shailesh\.ssh\id_rsa.pub

Use it in file as below is Azure VM resource block
~~~
admin_ssh_key {
    username   = "azureuser"
    public_key = file("C:\\Users\\Shailesh Singh/.ssh/id_rsa.pub")
~~~

# 📂 Deploy Website

## Copy website folder

```powershell
scp -i "C:\path\VMdemo_key.pem" -r website azureuser@<public-ip>:/home/azureuser/
```

---

## Move files to Nginx directory

```bash
sudo rm -rf /var/www/html/*
sudo cp -r /home/azureuser/website/* /var/www/html/
```

---

## Restart Nginx

```bash
sudo systemctl restart nginx
```

---

# 🌍 Access Website

Open in browser:

```text
http://<public-ip>
```

---

# ⚠️ Common Issues
## ❌ During apply , you get error for VM size type not available for your subscription or your location
So check for alternate locations and compatible sizes


## ❌ Website not loading

* Check port 80 is open in NSG

---

## ❌ SSH connection fails

* Check port 22
* Verify `.pem` path

---

## ❌ CSS/JS not loading

* Check relative paths in HTML

---

## ❌ Terraform errors

* Run:

```bash
terraform init -upgrade
```

---

# 🔐 Security Best Practices

* Do not upload `.pem` files to GitHub
* Use `.gitignore`:

```text
*.pem
.terraform/
terraform.tfstate
terraform.tfstate.backup
```

---

# 🧹 Cleanup

To destroy resources:

```bash
terraform destroy
```

---

# 🧠 Key Learnings

* Infrastructure as Code using Terraform
* Azure VM provisioning
* Nginx web server setup
* Secure SSH access
* Real-world DevOps deployment

---

# 💡 Interview Answer

> “I built a DevOps project where I provisioned an Azure VM using Terraform, installed Nginx, deployed a multi-file website, and exposed it via port 80 using NSG rules.”

---

# 🚀 Future Enhancements

* CI/CD pipeline (GitHub Actions)
* Docker containerization
* Load balancer setup
* HTTPS using domain + Certbot
* Kubernetes deployment

---

# 📬 Connect With Me

* LinkedIn: [https://www.linkedin.com/in/shailesh-kumar-singh-amdocs](https://www.linkedin.com/in/shailesh-kumar-singh-amdocs)

---

⭐ If you found this useful, feel free to star the repo!


