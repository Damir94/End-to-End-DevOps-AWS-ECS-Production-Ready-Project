
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

### Add Routes in the Private Route table, including adding Private Subnets in the Private Route table

![1_Hm_Z-aISwT90kZrcQ6WA_A](https://github.com/user-attachments/assets/26f5b98d-1acc-43be-a69e-302884e42c66)

![1_4fxarlL_SqrCiiGVMKDPQw](https://github.com/user-attachments/assets/03bcfe83-4b3a-46d8-b24f-179b756b5f21)

![1_l9NbFCG_P8EViO6ehmWQJw](https://github.com/user-attachments/assets/916fbc81-c27b-4b32-a6db-797d4dd9f999)

## Setup Database
### Create DB Subnet Group for RDS with Private Subnets

![1_ru6xA0Wd8wvQz3R-2CvArg](https://github.com/user-attachments/assets/1fc987a5-685d-446a-a8cc-17ad20113198)

![1_LVHI3-TiMWqnLPqgp8LOog](https://github.com/user-attachments/assets/21186cae-22aa-4f2c-b920-062f6ce747e6)

![1_EAgVvlTVdHgNhlZMqZPPVA](https://github.com/user-attachments/assets/c391875b-7f70-4782-8685-0e199bf9f4cd)

### Now, we have to create an RDS Cluster with a free tier

![1_7w62OvZnjDX1lO1E8STC3g](https://github.com/user-attachments/assets/f9fda02d-6db4-45c5-a4d7-ed4801b5ae6b)

![1_JothVyDLv3HdcyYGWB5B9Q](https://github.com/user-attachments/assets/6f9588f2-57e3-42c7-8b4c-dd3d7b94c778)

![1__dcwNxRYZPLmbdW5IsXdpg](https://github.com/user-attachments/assets/6e39713e-2338-4106-9ffb-f8c2c8e4c914)

![1_EDBUyX-NhVUmMsCnmbn2xA](https://github.com/user-attachments/assets/23a4319e-c4be-4b9a-bf55-7cee3a4d3510)

![1_EDBUyX-NhVUmMsCnmbn2xA](https://github.com/user-attachments/assets/47553b79-74a0-4037-929d-37b02a410c1e)

![1_O57MfTEsHsq5dP-gfv6klA](https://github.com/user-attachments/assets/8cc4a1cb-5274-4070-a462-05d1c429860e)

## Create a security group for RDS by clicking on Create New if not created.

### We will make the changes for ports and other Inbound/Outbound rules later.

![1_-GW0_w7DWVlwgBCFkK9z1Q](https://github.com/user-attachments/assets/6b1678d0-3ab6-4e70-8baa-0c3d3af7c28c)

![1_yUXNfCp4ZO69BZPDwlBKmQ](https://github.com/user-attachments/assets/2c2d2561-17cc-4201-ae6a-389805fb019a)

### RDS is ready

![1_RARLruAYLVGlhQIUqYoUQg](https://github.com/user-attachments/assets/14bd5314-b084-4af9-95e5-db9075dec115)

## Create Parameter Stores for the DB Credentials
- Add the DB Host of your RDS
- Keep the root path the same /myapp/db/<key>

![1_N6ZDWR_Ae6iEY95xoO9vpA](https://github.com/user-attachments/assets/3ea3076f-f08d-4e72-9406-2529127860fb)

### Add the DB name

![1_FPwioPK6nmuiTJq8D5uN2Q](https://github.com/user-attachments/assets/15560f7c-e068-492b-ab43-4c5b5b206181)

### Add the DB Password

![1_o_ga95n1IFzN8BILGowSxw](https://github.com/user-attachments/assets/3d4ecb19-6ed8-4dfb-90e1-9cd2c028831c)

### Add the DB username

![1_ZWjWFG9hwP_PtK_cIE7uyg](https://github.com/user-attachments/assets/b5d1d7d4-c300-40e0-9222-dfb24a9f9a66)

## Create the Backend and Frontend ECR Repo
### Backend Repo

![1_HLNhw9gLCSgRQmfJJi3E_Q](https://github.com/user-attachments/assets/72074fdd-3d07-4d38-a505-0a330acba874)

### Frontend Repo

![1_UtZC8SKr8DGRKCeL_6W-jQ](https://github.com/user-attachments/assets/d26ddb3d-84d0-4f4b-a459-40e8dbd2aad4)

### Both repos have been created

![1_BLk9IiY7YxU4Bjp3zbiEaA](https://github.com/user-attachments/assets/4aaa6f53-102d-40e2-93de-b8dfee4d882a)

## Configuring ECS Cluster
- Provide the name to the ECS Cluster

![1_JsRvsQi9fsFQ0VOSrpUtVA](https://github.com/user-attachments/assets/50a3ffc1-9f77-42cf-88bd-42f2a499e6bc)

![1_dkgg_TuQ_u5dJa5qt3aB9A](https://github.com/user-attachments/assets/a899d526-65bf-4810-94c3-0559924b2921)

- Currently, we can’t create any task definitions because there is no image present in our ECR repo.
- To do that, we have to push our image, so let’s build our first backend source code and push the Docker image to the ECR repo
- Here is the repo link: https://github.com/AmanPathak-DevOps/Student-Teacher-Portal-Three-Tier-Application/tree/ecs-deployment
- Make sure you select the ecs-deployment branch; other branches will get you into trouble.

![1_3c1QDZJqMI5zkfqeix2y6Q](https://github.com/user-attachments/assets/41e7f700-c14d-4146-b5e9-d23f4b8862fc)

## Now, here is the workflow for the backend

```bash
name: Backend Build & Push

on:
  workflow_dispatch:

jobs:
  build-push:
    runs-on: ubuntu-latest

    permissions:
      contents: read

    defaults:
      run:
        shell: bash
        working-directory: backend

    steps:
      - name: Checkout Code
        uses: actions/checkout@v6

      - name: Configure AWS
        uses: aws-actions/configure-aws-credentials@v5
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Login to ECR
        uses: aws-actions/amazon-ecr-login@v2

      - name: Build and Push
        uses: docker/build-push-action@v3
        with:
          context: backend
          path: backend/Dockerfile
          push: true
          tags: 615299766984.dkr.ecr.us-east-1.amazonaws.com/dev/backend:${{ github.run_number }}
```

- As you can see in the repo, two secrets will help us to authenticate with AWS ECR to push our image

![1_kWOLqhAUFovzrDR6qGv6NA](https://github.com/user-attachments/assets/29a444a0-b615-40b7-85ba-fee93dd8c327)

## Now, we will run our backend workflow and make sure to select the correct branch, i.e., ecs-deployment

![1_Xo5Aq6OMaZ7-Q94o5sImvw](https://github.com/user-attachments/assets/056495ff-2b5e-4836-8175-fe57185c83ac)

### Our workflow runs successfully

![1_ofy2r1cPrHgER0jn8eqcqw](https://github.com/user-attachments/assets/a27ac52f-e721-4f0f-a90f-652d38f3dabb)

### Here is the image pushed to the ECR repo

![1_R4ZOvERTG08SSawRhMrIIw](https://github.com/user-attachments/assets/309a2058-76b2-4e05-9952-245bc7b6c49a)

### Now, we have to create the Task Definitions for both our backend and frontend applications. It will be like a blueprint for the containers, like specifications of the containers

![1_ATdZAS8ycKOALVjbIY1irQ](https://github.com/user-attachments/assets/ca4792af-2e54-4db4-8b32-51d2f3efcf78)

## Specs of Task Definition

![1_pFxpb3uAHnxFf-KMsnHi8g](https://github.com/user-attachments/assets/eb1b9264-14e1-4f07-a96e-870f4ba8899d)

![1_VUpVTJ60eqhUfUwTx50EMQ](https://github.com/user-attachments/assets/fff3ee51-6bc6-4d18-99e4-a77a955af79c)

## Task Definition has been created

![1_3F6mRfXShoKngHZSN1GT2w](https://github.com/user-attachments/assets/f66896d1-1200-49ac-bbbd-f90dc28d5896)

## Create a Service in the ECS cluster for the frontend

![1_q_jozb3xdl1R_zfQMbp9bg](https://github.com/user-attachments/assets/18147cd6-f944-41db-996a-e2e8e92d3897)

## Specs for Backend service

![1_KrZqOkWXAtWg8DB4J7d3HQ](https://github.com/user-attachments/assets/1805a526-a6f8-4091-a9cc-27a27640fe0f)

![1_CgqBsC3_CzgrUJiNXDxhEw](https://github.com/user-attachments/assets/73ee4a71-4c97-41d3-b4fc-7446e116aec8)

![1_yzi5BrDi5uY9jDEiKh6FxA](https://github.com/user-attachments/assets/9bb6d183-67d5-48ce-8f74-a75deecb2781)

![1_ieyAwjniu0Q3gpSChHNU-g](https://github.com/user-attachments/assets/3f385609-0396-452e-b423-71b4e9c5f454)

![1_BVTvh2lWKf9D2otVP0GptQ](https://github.com/user-attachments/assets/9fedf367-10a0-4ea4-9a0c-4208f5502a26)

![1_OR8rFejC9j2pOGeM0idqsw](https://github.com/user-attachments/assets/fbd98728-d266-4662-bdf0-75668ea37ee1)

![1_xUy--13b7NcTLoX2-q8hZw](https://github.com/user-attachments/assets/aacb43ce-82cb-4d47-9f3c-388c450ec474)

## Our both containers are in a running state

![1_c84MQ1GSBakUj6UBTp5zFQ](https://github.com/user-attachments/assets/479dcb54-6e7c-4927-8314-b2629860ec9e)

### Check the logs for our containers

![1_VRw5LF34BaJ0t8x6Wcr_4Q](https://github.com/user-attachments/assets/416f01a2-db96-42cc-91e9-588625588407)

### Both services are running perfectly

![1_qy4r5hUWZAtzD8efMejd9w](https://github.com/user-attachments/assets/74624725-f62d-43a8-a043-9c782539a4c2)

### Here is the LoadBalancer for the backend

![1_dVGx3V39jw7MfunV5j8Wrw](https://github.com/user-attachments/assets/36cce94b-092c-4001-a2b5-ac0e8f20c63c)

### Now copy the Backend ALB DNS and follow ahead

## Frontend Deployment
### Add the Backend Endpoint in your GitHub Secrets, as we are providing that while building our Dockerfile

API_BASE_URL

![1_9dKODnxeo9i7son8E1v52g](https://github.com/user-attachments/assets/bd631b36-92bc-4811-8b6f-f3ddfab5b492)

## Fronted Workflow

```bash
name: Frontend Build & Push

on:
  workflow_dispatch:

jobs:
  build-push:
    runs-on: ubuntu-latest

    permissions:
      contents: read

    defaults:
      run:
        shell: bash
        working-directory: frontend

    steps:
      - name: Checkout Code
        uses: actions/checkout@v6

      - name: Configure AWS
        uses: aws-actions/configure-aws-credentials@v5
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Login to ECR
        uses: aws-actions/amazon-ecr-login@v2

      - name: Build and Push
        uses: docker/build-push-action@v3
        with:
          context: frontend
          path: frontend/Dockerfile
          push: true
          tags: 615299766984.dkr.ecr.us-east-1.amazonaws.com/dev/frontend:${{ github.run_number }}
          build-args: |
            REACT_APP_API_BASE_URL=${{ secrets.API_BASE_URL }}
```
## Now, we have to run the workflow for the frontend

![1_GKw2FWftiD-QIIqbYGTPfQ](https://github.com/user-attachments/assets/da076f8c-602f-471e-8637-08f51c75521a)

### The workflow successfully ran

![1_dbAQBkiik0c7cEl_zTPI_A](https://github.com/user-attachments/assets/af254815-b5fe-426c-9128-875eb52255c4)

### Here is the ECR Image for Frontend Docker

![1_CMxSzIOG0TgnC7OTN7RYHg](https://github.com/user-attachments/assets/0011547c-7be7-456e-b501-04ed1f3c0958)

### Now, we have to create the Task Definition for Frontend.

![1_Y3NNHV3bJxpMy0s0TFY2CQ](https://github.com/user-attachments/assets/4bf812fc-4386-4a86-ba37-0493e327b137)

Before creating a service for any tier. AWS will prompt you to have an execution Role so your service can have the privilege to talk or access other AWS services. In our case, our Service needs to get a few services, especially fetch values from Parameter Store. For that, we provided SSMFullAccess.

![1_AS938YSvyNmKngAtmPb_Dw](https://github.com/user-attachments/assets/9605bc52-69a6-4ac0-9adb-ce5514845b7a)

![1_X7aIlmu6RuF-kykxBvQh0Q](https://github.com/user-attachments/assets/e083f4cf-faaa-4dfd-a813-9411c2618728)

![1_stgIVkhW-6fiMCuEa2gI_Q](https://github.com/user-attachments/assets/0d885a58-0371-4a74-8456-d00c752f6c32)

![1_H4QYDBsC-89g86D8OK0ebw](https://github.com/user-attachments/assets/89dbcc5b-10d5-4cc4-90f0-5366545133d6)

![1_pd-yCwK3t8GMYG0XZlrfrQ](https://github.com/user-attachments/assets/a4ff286f-feaf-472e-91ab-d1342932d01d)

### Task Definition has been created

![1_IA1cuCXcmLNjDuVXVQBgqg](https://github.com/user-attachments/assets/0887525e-619d-45d8-ada0-083d5a5054ab)

### Now we have to create a frontend service

![1_yPonO81mx7LhsnDnnNKNfQ](https://github.com/user-attachments/assets/2eebc786-97c0-4de6-819c-4b52773b8cd9)

![1_rl2co9H8RK8nF5JaQaZUxA](https://github.com/user-attachments/assets/c1cf14f7-afb4-4f90-89c6-dc93ec6c9c7e)

![1_rl2co9H8RK8nF5JaQaZUxA](https://github.com/user-attachments/assets/b0d7f096-6067-436d-949d-3019daef6a1e)

![1_K_TQ06eWKCv9_i0Q-XGvKQ](https://github.com/user-attachments/assets/4660a667-f826-49cb-9d15-8ee97236006f)

### Our both task running for the Frontend service

![1_8G8uzZo_1N4mG-69hKHIzg](https://github.com/user-attachments/assets/d79d8212-7fae-4c28-92bb-8652ea08e9ea)

### Here is the Target Group, and we can see the targets are healthy for the TG.

![1_b4kP910RhWPd3vrkrm_WYA](https://github.com/user-attachments/assets/b5a2eb4d-4447-4089-bf9c-e1a09cc4a828)

Here is the Load Balancer for the frontend

![1_1t-iu2KrfEaundwciOZUkA](https://github.com/user-attachments/assets/3108a9b3-e6a6-4a15-9701-83db849528a1)

Now, we will add domain mapping to our Frontend Load Balancer. If you want, you can integrate ALB with CDN + WAF. Currently, I will be adding one domain with SSL So we can access the application legitimately.

So, now click on Add listener and provide details as shown in the snippet below.

![1_CShO0bl7iAu0xiT7w18fTA](https://github.com/user-attachments/assets/71c7b0d6-3242-404b-adc3-4f5c16e48c72)

![1_ZdHSzgnfBPrg8lRCFDk7-w](https://github.com/user-attachments/assets/ea765023-15ae-4d48-baae-882a6f41743f)

### Added to my DNS provider

![1_z4MzdGGQecgcIeN_-7hnVA](https://github.com/user-attachments/assets/50e1fd1e-4a27-4291-8a8b-fb1a9d64bbdf)

### Here we can see our application serving via my domain

![1_zed47dx8dtwzSfYTI3D69A](https://github.com/user-attachments/assets/e3ff3780-569b-4d31-a6b0-67944f55f451)

### The CRUD operation is working fine for the application for both the Teacher and the Student

![1_SOrW7eBPtrjW9ZacAisOVw](https://github.com/user-attachments/assets/9891d404-80a4-40fe-826f-1da4445c5424)

![1_osw7pQ2PbJ9QseA-Qtv9Gg](https://github.com/user-attachments/assets/b95f4644-1227-4193-82b9-44bf8f0fd6c2)

### Now we have to do the cleanup part
Follow the sequence to delete things one by one to avoid any extra cost
- ECS Cluster
- Tasking Definition from ECS Section (Deregister both TD(frontend and backend) one by one)
- Load Balancers (frontend & backend
- Target Groups (frontend & backend)
- RDS
- NAT Gateway
- Associated Security Group(RDS & Default SG)
- VPC (it will delete other associated services)
- Parameter Store
- ECR Repos

### Conclusion
This project gave me a deeper understanding of ECS deployments by bringing together containers, networking, CI/CD, and database connections in a single environment.

What begins as the simple task of “running a container” quickly evolves into a complete system that involves security, traffic management, and automation. Working through this end-to-end setup made all of these components much easier to grasp.
