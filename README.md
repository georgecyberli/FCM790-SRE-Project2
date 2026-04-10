# AWS Cloud Observability & Incident Response

**Topics:** AWS, Observability, CloudWatch, Site Reliability Engineering, Monitoring, Incident Response, DevOps

![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![Observability](https://img.shields.io/badge/Focus-Observability-blue)
![SRE](https://img.shields.io/badge/Focus-Site%20Reliability%20Engineering-green)
![Monitoring](https://img.shields.io/badge/Monitoring-CloudWatch-yellow)
![Alerting](https://img.shields.io/badge/Alerting-SNS-red)

---

> **Note:** This is **Part 2** of a comprehensive cloud SRE engineering project.  
> While Part 1 focused on provisioning a highly available AWS architecture, this phase focuses on **instrumenting that system with production-grade observability and alerting**.

---

## 📌 Project Overview

This project demonstrates a complete, production-grade **observability and monitoring stack** implemented on an AWS cloud architecture.

The goal was to instrument a live web application (deployed via an **Application Load Balancer, Auto Scaling Group, and Amazon RDS backend**) to provide deep, real-time visibility into system health and reliability.

By implementing the **Four Golden Signals of Site Reliability Engineering (SRE)**, I established automated alerting mechanisms and an interactive dashboard to rapidly detect and triage system degradation, ensuring high availability and seamless incident response.


## 🏗️ Architecture & Technologies

### Infrastructure

- Application Load Balancer (ALB)  
- Amazon EC2 (Auto Scaling Group)  
- Amazon RDS  

### Observability

- Amazon CloudWatch  
- CloudWatch Logs Insights  
- CloudWatch Agent  

### Alerting

- Amazon SNS (Simple Notification Service)  
- CloudWatch Metric Math  

### Core Concepts

- Four Golden Signals (Latency, Traffic, Errors, Saturation)  
- Service Level Objectives (SLOs)  
- Incident Response Runbooks  


## 🚀 Key Implementations

### 1. The Four Golden Signals & Log Analytics

Configured centralized log aggregation using **CloudWatch Logs Insights** to parse and analyze application and system data.

Developed custom queries to track:

- **Errors:** Filtered 5xx HTTP response codes to track application failures  
- **Latency:** Analyzed target response times to monitor user experience delays  
- **Traffic:** Monitored total request volume routed through the ALB  
- **Saturation:** Tracked resource exhaustion (e.g., "out of memory" or "disk full" events) to predict potential downtime  


### 2. Custom Metrics & SLO Alerting

Installed and configured the **CloudWatch Agent** on EC2 instances to expose internal operating system metrics (Memory and Disk utilization) not captured by default AWS metrics.

Established strict **Service Level Objectives (SLOs)** for system performance.

Developed custom **Metric Math expressions** to calculate real-time error percentages.

Built **CloudWatch Alarms** integrated with **Amazon SNS** to immediately page on-call engineers when:

- Error rate exceeded **1.0%**
- p99 latency exceeded **1500 ms**


### 3. Centralized Monitoring Dashboard

Designed a comprehensive **"30-second rule" triage dashboard (P2-Monitoring-Dashboard)** to provide immediate situational awareness during incidents.

#### Key Features

- **Dynamic Visualizations:**  
  Plotted p50, p95, and p99 latency bands to identify tail-end performance degradation  

- **Capacity Tracking:**  
  Displayed real-time CPU and Memory utilization across dynamically scaling EC2 instances  

- **Visual Thresholds:**  
  Implemented horizontal annotation lines to highlight when metrics cross critical SLO boundaries  


### 4. Incident Response & On-Call Handoff

To ensure production readiness, a comprehensive **On-Call Handoff Document (Runbook)** was created.

This includes:

- Architecture and critical endpoint overviews  
- First-response troubleshooting workflows for CloudWatch anomalies  
- Matrixed failure modes with direct remediation steps  

#### Example Failure Scenarios Covered

- Out-of-Memory (OOM) kills  
- RDS connection drops  
- Auto Scaling Group scale-out delays  

Designed for **rapid 3:00 AM incident triage**.


## 🧠 Key Takeaways

- Observability is not just monitoring — it enables **rapid root cause analysis and incident response**  
- The **Four Golden Signals** provide a reliable framework for tracking system health  
- Proactive alerting reduces downtime and improves system reliability  
- Well-documented runbooks are critical for real-world production environments  

---

<a href="https://github.com/georgecyberli/FCM790-SRE-Project1.git" class="button icon back">Back to Part 1</a>
