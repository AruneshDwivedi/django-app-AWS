### Deploying Django Application on AWS using ECS and ECR 🚀

This project focuses on deploying a Django-based web application onto AWS using **Elastic Container Service (ECS)** and **Elastic Container Registry (ECR)**. We will walk through the process of creating a Docker image for the Django app, pushing it to ECR, setting up ECS to manage containers, and finally ensuring the app runs smoothly on AWS. Let’s dive in! 👩‍💻✨

![proj_Overview](https://github.com/user-attachments/assets/dd20dbe6-064e-445c-84cc-8d81ab7d50e5)


---

#### Prerequisites 🎓
* **Django** (for web development)
* Basic knowledge of **Docker**
* An **AWS account**
* A touch of **creativity** 😊

---

### About Django 🐍

Django is a high-level Python web framework that encourages rapid development with clean and pragmatic design. It is free, open-source, and comes with tons of features—like great documentation, an active community, and extensive support options.

---

### What is Docker & Containers? 🚢
![flow of dckr](https://github.com/user-attachments/assets/9aae5ba1-33bd-4d55-a6eb-f2ffb0195ca6)

**Docker** allows you to package an application and its dependencies into a "container," which is a lightweight, isolated environment. It ensures your app will run smoothly regardless of where it is deployed. Docker makes development and shipping apps much more efficient! 💻

---

### What is AWS Elastic Container Registry (ECR)? 🛢️

**Amazon ECR** is a fully managed container image registry that simplifies storing and managing Docker images. It integrates perfectly with Docker CLI and supports both private and public repositories, ensuring that your images are easily accessible when needed.

---

### Step-by-Step Guide to Deploy 🛠️

#### 1. **Create a Docker File for Your Django App** 📝

Start by adding a **Dockerfile** to your Django app, specifying the commands needed to build the Docker image.

---

#### 2. **Build Docker Image** 🔨

Build the Docker image locally using the command below:

```
docker build -t hello-world-django-app:version-1 .
```

---

#### 3. **Verify Docker Image** ✅

Ensure that your image has been created with:

```
docker images | grep hello-world-django-app
```

---

#### 4. **Set Up Repository in AWS ECR** 🖥️

1. Log into the **AWS Console**, search for **ECR**, and click **Create Repository**.
2. Choose **Private** visibility (you can enable scanning to identify software vulnerabilities).
3. Push your Docker image to **ECR**.

---

#### 5. **Push Docker Image to ECR** 🚀

- First, authenticate Docker to ECR:
  
```
export AWS_ACCESS_KEY_ID=******  
export AWS_SECRET_ACCESS_KEY=******
```

- Login with the command:

```
aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com
```

- Tag your image for ECR:

```
docker tag 480903dd8 aws_account_id.dkr.ecr.region.amazonaws.com/hello-world-django-app
```

- Now push the image to ECR:

```
docker push aws_account_id.dkr.ecr.region.amazonaws.com/hello-world-django-app
```

---

### What is AWS Elastic Container Service (ECS)? 🚚

**Amazon ECS** allows you to easily run Docker containers in a highly scalable, secure environment. It helps in managing containerized applications using clusters of EC2 instances. ECS ensures that your app runs reliably and can scale as needed.

---

### Steps to Launch the Application on ECS 🚀

#### 1. **Create an ECS Cluster** 🌐

Start by creating a **cluster** in ECS using the AWS console. Choose your preferred region and define the settings for your cluster.

---

#### 2. **Launch EC2 Instance** 💻

Create EC2 instances under your ECS cluster for container management. Here you’ll configure things like network settings and Auto-Scaling groups.

---

#### 3. **Create ECS Service** 🚀

Configure a **service** within your ECS cluster that runs a task definition. This involves specifying the container settings, including the Docker image to use from ECR.

---

#### 4. **Create Task Definition** 🎯

Define your ECS **task**—it contains all information about what containers to run and their configurations, including what ports need to be opened for your app.

---

#### 5. **Run the Instance** 🎬

Once the task is configured, trigger the ECS task and see your Django app running on the instance. Check the **EC2** console to verify the instance is up and running.

---

### Celebrate! 🎉

**Mission Accomplished!** 🎯 We’ve successfully deployed the Django app on AWS using ECS and ECR. 🚀 You can now access it by navigating to the **public DNS** of your instance in the browser!

---

### Beyond the Basics 🔧

For a production-ready app, you need to think about:
* **Security** 🔒 (protecting your app and data)
* **Monitoring** 📊 (observing your app’s performance and health)
* **Load Balancing** ⚖️ (distributing traffic evenly across your app)
* **Recovery Plans** 🛡️ (ensuring your app stays available)

You can also streamline deployments with **AWS Elastic Beanstalk**.

---

### Wrapping Up ✨

Feel free to explore the full potential of deploying web apps using AWS, ECS, and Docker. I hope this project guide provides you the tools and knowledge to implement your own Django app on the cloud. 🌥️

---
  
Author: [Arunesh Dwivedi](https://github.com/AruneshDwivedi)
