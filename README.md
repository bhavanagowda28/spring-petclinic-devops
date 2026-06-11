# Spring PetClinic DevOps Project 🚀

## Overview
This project demonstrates end-to-end DevOps implementation by deploying the Spring PetClinic application using Docker, Docker Compose, AWS EC2, Nginx reverse proxy, and CI/CD automation.

The system follows a **three-tier architecture**:
User → Nginx → Spring Boot Application → MySQL Database

---

## Tech Stack
- Java 17 (Spring Boot)
- Maven
- Docker
- Docker Compose
- MySQL
- Nginx
- Jenkins (CI/CD)
- AWS EC2
- Git & GitHub

---

## Features
- Containerized Spring Boot application using Docker
- Multi-container setup using Docker Compose
- MySQL database integration
- Nginx reverse proxy configuration
- Deployed on AWS EC2 instance
- CI/CD pipeline using Jenkins
- Version control using GitHub

---

## Docker Commands
Build image:
docker build -t petclinic .

Run container:
docker run -d -p 8080:8080 --name petclinic-app petclinic

---

## Docker Compose
version: "3.8"

services:
  mysql:
    image: mysql:8
    container_name: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: petclinic
    ports:
      - "3306:3306"

  petclinic:
    image: petclinic
    container_name: petclinic-app
    ports:
      - "8080:8080"
    depends_on:
      - mysql

---

## Nginx Configuration
server {
    listen 80;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

---

## AWS Deployment
- EC2 Ubuntu instance used
- Security groups configured:
  - 22 (SSH)
  - 80 (HTTP)
  - 8080 (App access)
- Application accessed via public IP

---

## Screenshots
Add your screenshots inside `screenshots/` folder:

- EC2 Instance
- Docker Containers (docker ps)
- Docker Images
- Nginx Configuration
- Security Group
- Application UI (PetClinic)

Example:
![EC2](screenshots/ec2-instance.png)
![Docker](screenshots/docker-ps.png)
![Images](screenshots/docker-images.png)
![Nginx](screenshots/nginx-config.png)
![Security](screenshots/security-group.png)
![App](screenshots/petclinic-aws.png)

---

## Key Learnings
- Docker containerization
- Multi-container orchestration using Docker Compose
- Nginx reverse proxy setup
- AWS EC2 deployment
- CI/CD pipeline basics using Jenkins
- Real-world DevOps workflow

---

## Author
Bhavana S Gowda  
DevOps Engineer | AWS | Docker | Jenkins | Spring Boot
