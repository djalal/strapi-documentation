---
title: Artifakt Deployment - Strapi Developer Docs
description: How to deploy your Strapi application on AWS using Artifakt.
canonicalUrl: https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/artifakt.html
---

# Artifakt

This a step-by-step guide on how to deploy Strapi on [Artifakt](https://artifakt.com).

Artifakt helps developers deploy, host and manage their web applications on scalable and resilient cloud infrastructure.

Leveraging Artifakt for your Strapi applications removes the grunt work from cloud infrastructures, while ensuring good practices as advertised by DevOps principles.

::: note
For a quickstart, you can fork the demo repository at https://github.com/artifakt-io/demo-strapi. This contains all the boilerplate for a seamless integration with Artifakt deployments.

:::

## How will run your Strapi application on Artifakt?

Environments at Artifakt are automatically created with complete infrastructure components:
* **Networking** - ELB, VPC, 
* **Compute** - Instances
* **Storage** - Persistent Disk

As for Strapi, the default deployment options use a persistent disk to enable development. For production, see [instructions below](#production). 
* **Database** – SQLite is installed on a persistent storage.
* **Content-type builder** – the builder is enabled by default for convenience.
* **APIs** – as Strapi generates code through the WebUI, the resulting files are stored in persisted storage.
* **Uploads** – Assets can be uploaded, and also part of the persistent volume.

### Strapi Logs
The Strapi application logs are stored in CloudWatch Logs. Logs can be monitored from the Fargate console under tasks. The default log retention is 90 days.

## Deploy Strapi Infrastructure
Artifakt provides a built-in environment template that provisions the necessary infrastructure to run Strapi on your AWS account in a scalable, secure, and reliable way with zero downtime deployment.

### 1. Connect to Artifakt Console
Open [Artifakt Console](https://portal.Artifakt.com/register) to login. If you don't have one already, ask us for a free invitation.

### 2. Create a project
On the left sidebar, add a project by clicking _Create project_. After you choose a name, and a cloud region, make sure the "NodeJs" runtime is set, on version 14. Confirm by clicking _Create project_ in the modal.

### 3. Connect a git repository
On the next screen, select your git provider, and point to the exact repository and point to the default branch.

### 4. Create an environment 
Click the _New Environment_ button on the top right corner. In the modal popup, pick a custom name, and click "Create and Start". This will provision all the underlying infrastructure, from load balancer to nodes. Depending on conditions, it can take between 3 to 7 minutes.

### 4. Settings configuration
Before deployment, the last step is to declare variables to configure Strapi. Click on Settings, and then on Build&Deploy.
Here is a list of variables to enter.
- NODE_ENV=development
- HOST=0.0.0.0
- PORT=80
- APP_KEYS=3BP8Udb7GNwxhfoTZjS98A==,wLyP+sc7hX7i33vAYglVoQ==,ZzswfDPpEYEq1s3Y1JW/4Q==,RqRLamF+7qGPjn6rkPM3ng==
- JWT_SECRET=6376f444-7e51-432a-b548-6e08621e6093
- API_TOKEN_SALT=6ee488fe1379c02794357ae9206484ca
- DATABASE_FILENAME=/data/artifakt.db

After that, hit the _Save_ button.

### 6. Deploy the environment
Finally, to deploy the environment, go to the "Jobs" section, and click the Run Job button. In the selection, pick the _Build and Deploy_ job and hit _Run job_

It takes up to 10 minutes to complete the process.

Once the deployment job completes, you can reach the live URL by clicking on the green arrow next to the environment name in the top header of the window.


## Production settings

### Provision a database server
TBD

### Configuring a custom domain
TBD


