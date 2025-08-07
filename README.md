# HOTSTAR APPLICATION PROJECT 🚀

This is a real-time **Hotstar Clone Application** DevOps project deployed using CI/CD on AWS.

---

## 🔧 Tools Used

| Tool        | Purpose                                  |
|-------------|-------------------------------------------|
| **AWS EC2**     | Cloud servers for hosting components     |
| **Git & GitHub** | Source code management & version control |
| **Jenkins**   | CI/CD pipeline automation                |
| **Maven**     | Build and package Java application       |
| **SonarQube** | Code quality analysis                    |
| **Nexus**     | Artifact storage                         |
| **Tomcat**    | Application deployment server            |

---

## 🧠 Why Jenkins Master-Slave Architecture?

Using **Jenkins Master-Slave** architecture distributes CI/CD tasks across multiple agents, providing:

- Better performance and scalability
- Isolation of environments/toolchains per project
- Efficient resource utilization

---

## 🔥 Step-by-Step Guide

### ✅ Step 1: Create AWS Instances
Create two instances from AWS Console:
- `t2.medium` (Master)
- `t2.micro` (Slave)  
Ubuntu OS for both.

![Step 1](https://github.com/user-attachments/assets/68d6308a-3f6b-423f-bc51-da7985cc0030)

---

### ✅ Step 2: Connect to Instances via MobaXterm

Login to both instances using **public IP** and **.pem key**.

![Step 2](https://github.com/user-attachments/assets/cf4f8a9b-4715-44a8-b3ca-3c7767f198a9)

---

### ✅ Step 3: Install Required Tools

- **Master Node:** Java 17, Jenkins, Nexus, SonarQube  
- **Slave Node:** Java 17, Git, Maven, Tomcat

![Step 3](https://github.com/user-attachments/assets/3c50f866-df6a-4f23-aa24-7c041c40f460)

---

### ✅ Step 4: Access Dashboards

- Jenkins, Nexus, SonarQube → via Master Node IP  
- Tomcat → via Slave Node IP (port `8080`)

![Jenkins/Nexus](https://github.com/user-attachments/assets/04f9eca9-045c-4c38-b0ed-0a275eff8da0)
![Tomcat](https://github.com/user-attachments/assets/a9815d14-7d28-4783-ba27-d1409afc6a00)

---

### ✅ Step 5: Install Jenkins Plugins

Install necessary plugins from Jenkins dashboard.

![Plugins](https://github.com/user-attachments/assets/0a7fec43-4f94-49b2-8cd0-84f2cb4a1be8)

---

### ✅ Step 6: Configure Global Tools

Set up **JDK, Maven, Git, and SonarQube Scanner** under Jenkins Global Tools.

![Tool Config](https://github.com/user-attachments/assets/2c017723-5fda-4212-9a49-ca3de3f1d4f6)

---

### ✅ Step 7: Setup SonarQube Token & Webhook

Generate a token and create webhook for code analysis.

![SonarQube Token](https://github.com/user-attachments/assets/2abaee6c-2639-4175-bcdb-c24d9146dba4)

---

### ✅ Step 8: Add Credentials in Jenkins

Manage your secrets via **Manage Jenkins → Credentials**.

![Credentials](https://github.com/user-attachments/assets/86606fb6-d661-48f1-962d-b733c02ced63)

---

### ✅ Step 9: Configure SonarQube Server in Jenkins

Add SonarQube instance under Jenkins → Configure System.

![Sonar Config](https://github.com/user-attachments/assets/ca4eebc8-cb1e-40b2-af69-7d9ed2458300)

---

### ✅ Step 10: Add Slave Node to Jenkins

Add Slave under **Manage Jenkins → Nodes**, configure using **SSH and private key**.

![Node Setup](https://github.com/user-attachments/assets/ca2e45f2-6d24-4022-b260-df93f3c64ae8)

---

### ✅ Step 11: Create CI/CD Pipeline in GitHub Repo

Create `Jenkinsfile` in the repo with all stages:
- Git clone
- Build (Maven)
- SonarQube analysis
- Nexus push
- Tomcat deployment

📝 **Refer to Jenkinsfile in project repository**

---

### ✅ Step 12: Create Pipeline Job in Jenkins

- Create new item → Pipeline  
- Link to GitHub repo  
- Click **Build Now**

![Build Start](https://github.com/user-attachments/assets/47bedfff-f3f6-46bc-a64d-27813a3459ed)
![Build Console](https://github.com/user-attachments/assets/c1d3414a-0424-4c11-80c1-d1986c154d77)

---

### ✅ Step 13: Verify in Tomcat

Open Tomcat Web UI → Check for deployed application.

![Tomcat Deployment](https://github.com/user-attachments/assets/3a0aa020-d8ae-40c2-80ed-f77517c2100c)

---

### ✅ Step 14: Open Application

Click on the application label to view the **Home Page** — successful deployment!

![App Home](https://github.com/user-attachments/assets/26a6cd3a-9e24-49c3-83b5-7431a8ea4107)

---

## ✅ Conclusion

This project demonstrates a **complete CI/CD pipeline setup** using Jenkins, with automated code analysis, artifact management, and deployment to Tomcat, leveraging **Master-Slave Architecture** for scalability.

---

## 📁 Project Folder Structure (Example)

hotstar-app/
├── src/
├── Jenkinsfile
├── pom.xml
└── README.md

Created by 

Padmarao Jonna | AWS DevOps Engineer🔗 GitHub Profile🔗 LinkedIn
Note: I have also given the Dockerfile and its Jenkinsfile in this repository, we you want to deploy using Docker container  
