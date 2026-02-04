# AWS CI/CD Pipeline with Jenkins & Ansible

## 📌 Project Overview
This project demonstrates an end-to-end CI/CD pipeline for Java applications using Jenkins, GitHub Webhooks, Maven, Ansible, and AWS EC2.

## 🛠 Tech Stack
- AWS EC2
- Jenkins
- GitHub
- Maven
- Ansible
- Docker
- Prometheus & Grafana

## CI/CD Architecture Overview
                     ┌─────────────────────────┐
                     │       Developer          │
                     │   (Git Commit / Push)    │
                     └───────────┬─────────────┘
                                 │
                                 ▼
                     ┌─────────────────────────┐
                     │        GitHub Repo       │
                     │  (Source Code + Jenkinsfile)
                     └───────────┬─────────────┘
                                 │
                         GitHub Webhook
                                 │
                                 ▼
          ┌─────────────────────────────────────────┐
          │            Jenkins Server (EC2)          │
          │------------------------------------------│
          │  • Multibranch Pipeline                  │
          │  • Jenkinsfile (Pipeline as Code)        │
          │  • Maven Build Automation                │
          │  • Docker Image Build                    │
          │  • Ansible Deployment Trigger            │
          └───────────────┬─────────────────────────┘
                          │
                 WAR Artifact + SSH
                          │
                          ▼
          ┌─────────────────────────────────────────┐
          │          Tomcat Server (EC2)              │
          │------------------------------------------│
          │  • Java Web Application                  │
          │  • Automated Deployment                  │
          │  • Production Runtime                    │
          └───────────────┬─────────────────────────┘
                          │
                    HTTP Traffic
                          │
                          ▼
                 ┌──────────────────────┐
                 │     End Users         │
                 │  (Browser Requests)  │
                 └──────────────────────┘


============================================================

                 MONITORING & OBSERVABILITY LAYER

============================================================

      Jenkins EC2                           Tomcat EC2
          │                                    │
     Node Exporter                        Node Exporter
          │                                    │
          └───────────────┬────────────────────┘
                          │
                          ▼
               ┌────────────────────────┐
               │       Prometheus         │
               │  (Metrics Collection)   │
               └───────────┬────────────┘
                           │
                           ▼
               ┌────────────────────────┐
               │        Grafana           │
               │   (Visualization UI)    │
               └────────────────────────┘

## Workflow Diagram

![alt text](<Workflow Diagram.png>)

## ⚙ Features
- Automated build and deployment
- Webhook triggered pipeline
- Infrastructure automation
- Monitoring integration
- Zero manual deployment

## 🚀 Deployment Steps
1. Launch EC2 instances
2. Install Jenkins & dependencies
3. Configure webhook
4. Setup pipeline
5. Deploy application

## 📊 Output Screenshots
![alt text](<Screenshot 2026-01-27 141844.png>)![alt text](<Screenshot 2026-01-27 142018.png>)![alt text](<Screenshot 2026-01-28 200718.png>)

## ✅ Learning Outcomes
- CI/CD automation
- Production DevOps workflow
- Infrastructure management
