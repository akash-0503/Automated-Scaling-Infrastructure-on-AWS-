# ⚙️ Automated Scaling Infrastructure on AWS

## 🧠 Objective

This project demonstrates how to build an **automated, scalable, and fault-tolerant infrastructure on AWS**. The goal is to ensure that compute resources scale **dynamically** based on incoming traffic or usage patterns, optimizing for **cost** and **performance**.

---

## 🏗️ Architecture Overview

### 🔁 Flow:

1. **Users** send requests to the application.
2. Requests hit the **Application Load Balancer (ALB)**.
3. The ALB distributes traffic to one or more **EC2 instances** inside an **Auto Scaling Group**.
4. **CloudWatch** monitors resource metrics (e.g., CPU utilization).
5. Based on **scaling policies**, EC2 instances are automatically **added or removed**.
6. New instances are registered with the Load Balancer seamlessly.

---

### 🖼️ Diagram
            +------------------------+
            |      Users/Clients     |
            +----------+-------------+
                       |
                       v
      +-------------------------------+
      |  Application Load Balancer    |
      +-------------------------------+
                |           |
                v           v
      +-------------------+ +-------------------+
      |   EC2 Instance 1  | |   EC2 Instance n  |
      +-------------------+ +-------------------+
                 |               |
                 +--> CloudWatch <---+
                       Metrics        |
                 +-------------------+
                 | Auto Scaling Group|
                 +-------------------+


