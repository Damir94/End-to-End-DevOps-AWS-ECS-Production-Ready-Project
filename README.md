# End to End DevOps AWS ECS Production Ready Project

![1_TOB4EEdDKBEqI5Y0NwJ-2Q](https://github.com/user-attachments/assets/0f5b2819-e4d8-4ad3-8ff3-3f57acfc7ac2)

## Introduction
Modern cloud deployments go far beyond simply running containers. In real-world environments, you need components like networking, CI/CD pipelines, secrets management, database connectivity, and a scalable architecture.

In this project, I designed and implemented a complete end-to-end deployment on AWS ECS for a three-tier application, with the goal of understanding how production-grade systems operate beyond basic demos.

Rather than focusing solely on containerization, this project covers the full lifecycle—from code to cloud—including image building, secure configuration management, load balancing, and private networking.

If you're exploring ECS, DevOps, or AWS architecture, this project provides a practical, hands-on perspective on how all these components come together in a real deployment.

### What We’ll Build
In this guide, we’ll deploy a three-tier application on AWS using a production-style architecture.

The solution includes:
- Frontend and backend services running on Amazon ECS
- Container images stored in Amazon EC
- A MySQL database hosted on Amazon RDS within private subnet
- Secure credential management using Parameter Store
- Automated CI/CD workflows with GitHub Actions
- An Application Load Balancer to route traffic to service
- A VPC design with both public and private subnets
By the end, you’ll have a fully functional deployment and a solid understanding of how ECS-based applications are structured in real-world environments.

Prerequisites:
- Before getting started, you should have:
- A basic understanding of AWS services such as ECS, VPC, and RDS
- An AWS account with permissions to provision networking and compute resource
- Docker installed locally for building container image
- A GitHub account for setting up CI/CD pipeline
- Familiarity with basic CLI usage and environment configuration
You don’t need deep expertise in ECS—this guide walks you through the key concepts along the way.

## HandsOn
### Create Networking services

![1_IUpNyJ2yTV6kO9OTljGFng](https://github.com/user-attachments/assets/785dece4-fedf-4fe9-b89b-d20f4388b7dd)

![1_BH_Ww1QiYKJrvPSHNu6TXA](https://github.com/user-attachments/assets/e486e346-16db-404f-9873-3aa3fd3b800a)

### Verify Networking services

![1_g_FXnwyxmTEHsqHzMvrtyg](https://github.com/user-attachments/assets/b3274ffb-ebb0-42af-9a7e-6a84658f8fd8)

### Create a NAT Gateway and configure

![1_uDHK-SowUJXdiKuRptShyg](https://github.com/user-attachments/assets/08495c90-5ab2-4c87-8d4e-e1b1c639f221)

![1_Ae7L9BtnplEzz2T-2DV_pw](https://github.com/user-attachments/assets/56db46e2-17e3-4414-8d4f-951147b0b1c0)

![1_pYeWC8KiFi1JJNUa97nXmw](https://github.com/user-attachments/assets/5e4e51ea-a7a2-4af5-9490-85a04d424e09)

Add Routes in the Private Route table, including adding Private Subnets in the Private Route table

![1_Hm_Z-aISwT90kZrcQ6WA_A](https://github.com/user-attachments/assets/26f5b98d-1acc-43be-a69e-302884e42c66)

![1_4fxarlL_SqrCiiGVMKDPQw](https://github.com/user-attachments/assets/03bcfe83-4b3a-46d8-b24f-179b756b5f21)

![1_l9NbFCG_P8EViO6ehmWQJw](https://github.com/user-attachments/assets/916fbc81-c27b-4b32-a6db-797d4dd9f999)

