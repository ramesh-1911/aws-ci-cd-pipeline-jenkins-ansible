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

This architecture implements an event-driven CI/CD pipeline on AWS EC2 where 
GitHub webhooks trigger Jenkins Multibranch Pipeline to automatically build 
applications using Maven and deploy them to a remote Tomcat server using Ansible. 
Infrastructure and pipeline metrics are collected by Prometheus and visualized 
using Grafana dashboards.
