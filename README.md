# DevSecOps CI/CD Pipeline

This project demonstrates a robust DevSecOps-driven CI/CD pipeline deployed on an AWS EC2 Ubuntu instance. The pipeline seamlessly integrates automated code quality checks, advanced vulnerability scanning, and containerized deployment workflows to ensure a secure and efficient development lifecycle.

---

## 📌 Project Overview

- Comprehensive automation of build, test, and deployment processes using industry-leading tools:
  - **Jenkins (CI/CD Orchestrator):** Automates all stages of the pipeline
  - **SonarQube:** In-depth static code analysis for bugs, vulnerabilities, and code smells
  - **OWASP Dependency Check:** Identifies vulnerable dependencies using the CVE database
  - **Trivy:** Conducts thorough vulnerability scans on files, Docker images, and filesystems
  - **Docker & Docker Compose:** Reliable, scalable containerized application deployment
  - 
![WhatsApp Image 2025-09-12 at 9 35 02 PM](https://github.com/user-attachments/assets/02d06aa4-367b-44aa-8f7d-6d1fd596cf0f)

## ⚙️ Tooling & Capabilities

- **Jenkins**
  - Enterprise-grade Continuous Integration/Continuous Delivery platform
  - Orchestrates pipeline stages via extensible plugins (SonarQube, OWASP, Docker, etc.)

- **SonarQube**
  - Static Application Security Testing (SAST)
  - Automated detection of bugs, vulnerabilities, and maintainability issues
  - Enforcement of Quality Gates to prevent insecure builds

- **OWASP Dependency Check**
  - Deep analysis of project dependencies
  - Flags libraries with known security vulnerabilities

- **Trivy**
  - Fast, open-source vulnerability scanner
  - Multi-target scanning:
    - File System
    - Docker Images
    - Git Repositories
  - Generates comprehensive HTML/JSON reports

- **Docker & Docker Compose**
  - Docker: Industry-standard containerization for applications and services
  - Docker Compose: Declarative multi-container orchestration for complex deployments

## ☁️ Infrastructure on AWS

- **EC2 Instance Configuration**
  - AMI: Ubuntu
  - Instance Type: m7i-flex.large
  - Root Volume: 30 GB (EBS)
  - Security Group: Open ports 22 (SSH), 8080 (Jenkins), 9000 (SonarQube)

- **System Prerequisites**
  - `sudo apt-get update`
  - `sudo apt-get install openjdk-11-jdk -y`  # Required for Jenkins
  - `sudo apt-get install docker.io docker-compose -y`

- **Jenkins Installation**
  - Runs on port 8080
  - Initial setup with admin credentials and essential plugins

- **SonarQube Deployment (Docker)**
  - `docker run -d --name sonarqube-server -p 9000:9000 sonarqube:lts-community`

- **Trivy Installation**
  - `sudo apt-get install wget apt-transport-https gnupg lsb-release -y`
  - `wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -`
  - `echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee /etc/apt/sources.list.d/trivy.list`
  - `sudo apt-get update`
  - `sudo apt-get install trivy -y`

## 🔗 Integrations & Configuration

- **Jenkins ↔ SonarQube**
  - Install SonarQube Scanner plugin in Jenkins
  - Generate a token in SonarQube (My Account → Security → Tokens)
  - Add token in Jenkins (Manage Jenkins → Credentials)
  - Configure SonarQube server details in Jenkins global settings
  - Set up SonarQube webhook for Jenkins:  
    `http://<jenkins-public-ip>:8080/sonarqube-webhook/`

- **Key Jenkins Plugins**
  - SonarQube Scanner
  - OWASP Dependency Check
  - Docker
  - Quality Gates

## 🔄 CI/CD Pipeline Workflow

- **Pipeline Defined in Jenkinsfile (Declarative Syntax):**
  1. **Source Code Checkout:** Clone repository from GitHub
  2. **Static Code Analysis:** Execute SonarQube Scanner to detect bugs, code smells, vulnerabilities
  3. **Dependency Security Scan:** Run OWASP Dependency Check for CVE vulnerabilities
  4. **Quality Gate Enforcement:** Validate build against SonarQube Quality Gates
  5. **Vulnerability Assessment:** Use Trivy to scan project directory and generate reports
  6. **Containerized Deployment:** Deploy services using Docker Compose for scalable execution

---

This pipeline exemplifies best practices in DevSecOps, combining automation, security, and reliability for modern software delivery on AWS.





![WhatsApp Image 2025-09-12 at 2 23 33 PM (1)](https://github.com/user-attachments/assets/a28c7673-bd9a-43e1-b711-027ab9d33348)
Our project enforces continuous code quality checks through SonarQube.
The latest analysis confirms:

0 Bugs 🐞

0 Vulnerabilities 🔒

0 Code Smells 🧹

0% Duplication 📉

Overall Grades: Reliability (A) | Security (A) | Maintainability (A)



🚀 With every commit, SonarQube automatically analyzes our codebase, ensuring it stays clean, secure, and production-ready.



