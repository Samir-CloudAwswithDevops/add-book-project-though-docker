<img width="1920" height="1080" alt="Screenshot (357)" src="https://github.com/user-attachments/assets/caf26d2e-58fb-48e7-a1aa-0d8d681c511a" />
<img width="1920" height="1080" alt="Screenshot (358)" src="https://github.com/user-attachments/assets/c1883e37-923c-4ac9-b88b-68c118123cf7" />

📚 Book Project Deployment using Docker & AWS

This guide explains how to deploy the Add Book Project using AWS RDS, EC2, and Docker.

🚀 1. Create Amazon RDS (MySQL)
👉 Steps:

Go to RDS Console → Click Create database

Choose MySQL engine → Full configuration

Version: MySQL 8.0.x

Template: Free tier (if eligible) or Dev/Test

Master username: admin

Master password: (your strong password)

Instance size: db.t3.micro

Connectivity:

VPC: default

Subnet group: default or custom

Security group: allow inbound port 3306 from EC2

Public access: Yes

Click Create Database

🖥️ 2. Launch EC2 Instance
👉 EC2 Configuration:

Instance type: c7i.large (or your choice)

Key pair: create/select existing

Attach IAM Role: AmazonEC2FullAccess

Security Group: allow inbound 22, 80, 82, 84

Connect using SSH

🔧 3. Install Required Packages on EC2
sudo su -
yum install docker -y
systemctl start docker
systemctl enable docker
yum install git -y
yum install mariadb105-server -y
📥 4. Clone Project
git clone https://github.com/Samir-CloudAwswithDevops/add-book-project-though-docker.git
cd add-book-project-though-docker/backend

Edit SQL file:

vi test.sql
# replace <rds-endpoint> and password
:wq!
🛢️ 5. Import Database into RDS
mysql -h <rds-endpoint> -u admin -p < test.sql
# password: Samir

Test:

show databases;
show tables;
select * from books;
🐳 6. Build & Run Backend Docker Container
cd backend
docker build -t backend .
docker run -dt -p 84:80 backend

Check:

docker ps
docker images

Open in browser:

http://<EC2-Public-IP>:84

Should show: Hello

🌐 7. Update Frontend Config
cd ../client/src/pages
vi config.js
# update API URL → http://<EC2-Public-IP>:84
:wq!
🐳 8. Build & Run Frontend Docker Container
cd ../../client
docker build -t frontend .
docker run -dt -p 82:80 frontend

Check:

docker ps
docker images

Open in browser:

http://<EC2-Public-IP>:82

🎉 Deployment Complete! Your Book App is Live.
 
