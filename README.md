# TODO-Django-CICD

## Introduction

Welcome to the "TODO-Django-CICD" project! This guide will walk you through setting up the project locally, on AWS EC2, and using Docker containers. This Django-based TODO application includes a Continuous Integration and Continuous Deployment (CI/CD) pipeline for an efficient development workflow.

## Pre-requisites:

Before you begin, make sure you have the following installed:
Git
Python (with virtualenv)
Docker
Jenkins
Access to an AWS EC2 instance


### Local Setup (VS Code)
1. Clone the Repository:

git clone https://github.com/Akashdhengale/django-todo-cicd.git
This command clones the project repository from the specified URL.

2. Setup Python Virtual Environment:
   
a. Install virtualenv:

```
pip install virtualenv
```

This command installs the virtualenv package, which is used to create isolated Python environments.

b. Create and activate a virtual environment:

```
python -m venv env
```

```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\env\Scripts\activate
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Default
```

These commands create a virtual environment named "env" and activate it.

3. Install Django:

```
pip install django
```

This command installs the Django framework within the virtual environment.

4. Run Django Commands:
   
a. Apply database migrations:

```
python manage.py makemigrations
python manage.py migrate
```

These commands apply database migrations to set up the database for the project.

b. Create a superuser for admin access:

```
python manage.py createsuperuser
```

This command prompts you to enter a username, email, and password for the superuser account.

c. Start the development server:

```
python manage.py runserver
```

This command runs the development server locally, and you can access the application at http://127.0.0.1:8000.

5. Create Requirement.txt:

```
pip freeze > requirements.txt
```

This command generates a file named "requirements.txt" containing a list of all installed Python packages and their versions.

## AWS EC2 Setup

1. SSH into Server:

```
mkdir project
```
![AWS Git Clone Snap](C:/Akash-TODO-Snap/AWS git clone snap.png)





```
cd project
```
```
git clone https://github.com/LondheShubham153/django-todo-cicd.git
```

These commands connect to the AWS EC2 instance, create a project directory, and clone the project repository.

2. Install Dependencies:
a. Install Python and pip:

sudo apt install python3-pip
This command installs Python3 and pip, the package installer for Python.

b. Install Django:

pip3 install django
This command installs the Django framework globally on the AWS EC2 instance.

3. Run Django Commands:
a. Start the server with external access:

python3 manage.py runserver 0.0.0.0:8000
This command runs the Django server with external access on port 8000.

b. Apply database migrations:

python manage.py migrate
This command applies database migrations to set up the database for the project.

Docker Container Setup
1. Kill Process on Port 8000:
a. Find the process using port 8000:

lsof -i:8000
This command lists the process using port 8000.

b. Kill the process using the obtained PID:

kill -9 <PID>
This command forcefully terminates the process using the specified PID.

2. Install Docker:
a. Update package lists and install dependencies:

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
These commands update package lists and install required dependencies.

b. Install Docker components:

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
These commands set up Docker's GPG key and configure the package manager.


echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
These commands add the Docker repository, update package lists, and install Docker components.

3. Build and Run Docker Container:
a. Build Docker image:

sudo docker build . -t todo-app
This command builds a Docker image named "todo-app" from the current directory.

b. Run Docker container:

sudo docker run -d -p 8000:8000 todo-app
This command runs the Docker container in detached mode, mapping port 8000.

Continuous Integration and Deployment (CI/CD) Pipeline with Jenkins
1. Install Jenkins:
bash
Copy code
sudo apt update && sudo apt upgrade -y
sudo apt install default-jre -y && sudo apt install default-jdk -y
These commands update package lists and install Java Runtime Environment (JRE) and Java Development Kit (JDK) for Jenkins.

2. Install Jenkins on Ubuntu 20.04:
bash
Copy code
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
These commands add the Jenkins GPG key, configure the package manager, update package lists, and install Jenkins.

3. Start Jenkins Service:
bash
Copy code
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
These commands enable Jenkins to start on boot, start the Jenkins service, and check its status.

4. Configure Jenkins:
Open Jenkins on http://ip:8080
Create a Jenkins agent.
Integrate GitHub with Jenkins under system < configure < find GitHub.
5. Create Jenkins Job:
Name: todo-app
Version Control: Git
GitHub Repo: [Your GitHub Repo]
Branch: develop
Add Build Steps:
bash
Copy code
sudo docker build . -t todo-app
sudo docker run -d -p 8000:8000 todo-app
6. Run Jenkins Job:
Click on "Build Now" in Jenkins. After a successful build
User
also add introduction and conclusion in above readme
ChatGPT
Certainly! Here's the updated README with added introduction and conclusion sections:

README for TODO-Django-CICD
Introduction
Welcome to the "TODO-Django-CICD" project! This comprehensive guide will walk you through the step-by-step process of setting up and running a Django-based TODO application locally, on AWS EC2, and within Docker containers. In addition, we'll explore the integration of Continuous Integration and Continuous Deployment (CI/CD) pipelines using Jenkins to enhance your development workflow.

Prerequisites
Before you begin, ensure that you have the following tools and dependencies installed on your system:

Git
Python (with virtualenv)
Docker
Jenkins
Access to an AWS EC2 instance
Local Setup (VS Code)
1. Clone the Repository:
bash
Copy code
git clone https://github.com/Akashdhengale/django-todo-cicd.git
Clone the project repository from the specified URL.

2. Setup Python Virtual Environment:
a. Install virtualenv:
bash
Copy code
pip install virtualenv
Install the virtualenv package, allowing you to create isolated Python environments.

b. Create and activate a virtual environment:
bash
Copy code
python -m venv env
.\env\Scripts\activate  # On Windows
Create a virtual environment named "env" and activate it.

3. Install Django:
bash
Copy code
pip install django
Install the Django framework within the virtual environment.

4. Run Django Commands:
a. Apply database migrations:
bash
Copy code
python manage.py makemigrations
python manage.py migrate
Apply database migrations to set up the database for the project.

b. Create a superuser for admin access:
bash
Copy code
python manage.py createsuperuser
Create a superuser account by providing a username, email, and password.

c. Start the development server:
bash
Copy code
python manage.py runserver
Run the development server locally, accessible at http://127.0.0.1:8000.

5. Create Requirement.txt:
bash
Copy code
pip freeze > requirements.txt
Generate a file named "requirements.txt" containing a list of installed Python packages and their versions.

AWS EC2 Setup
1. SSH into Server:
bash
Copy code
ssh into server
mkdir project
cd project
git clone https://github.com/LondheShubham153/django-todo-cicd.git
Connect to the AWS EC2 instance, create a project directory, and clone the project repository.

2. Install Dependencies:
a. Install Python and pip:
bash
Copy code
sudo apt install python3-pip
Install Python3 and pip, the package installer for Python.

b. Install Django:
bash
Copy code
pip3 install django
Install the Django framework globally on the AWS EC2 instance.

3. Run Django Commands:
a. Start the server with external access:
bash
Copy code
python3 manage.py runserver 0.0.0.0:8000
Run the Django server with external access on port 8000.

b. Apply database migrations:
bash
Copy code
python manage.py migrate
Apply database migrations to set up the database for the project.

Docker Container Setup
1. Kill Process on Port 8000:
a. Find the process using port 8000:
bash
Copy code
lsof -i:8000
List the process using port 8000.

b. Kill the process using the obtained PID:
bash
Copy code
kill -9 <PID>
Forcefully terminate the process using the specified PID.

2. Install Docker:
a. Update package lists and install dependencies:
bash
Copy code
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
Update package lists and install required dependencies.

b. Install Docker components:
bash
Copy code
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
Set up Docker's GPG key and configure the package manager.

bash
Copy code
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Add the Docker repository, update package lists, and install Docker components.

3. Build and Run Docker Container:
a. Build Docker image:
bash
Copy code
sudo docker build . -t todo-app
Build a Docker image named "todo-app" from the current directory.

b. Run Docker container:
bash
Copy code
sudo docker run -d -p 8000:8000 todo-app
Run the Docker container in detached mode, mapping port 8000.

Continuous Integration and Deployment (CI/CD) Pipeline with Jenkins
1. Install Jenkins:
bash
Copy code
sudo apt update && sudo apt upgrade -y
sudo apt install default-jre -y && sudo apt install default-jdk -y
Update package lists, install Java Runtime Environment (JRE), and Java Development Kit (JDK) for Jenkins.

2. Install Jenkins on Ubuntu 20.04:
bash
Copy code
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
Add the Jenkins GPG key, configure the package manager, update package lists, and install Jenkins.

3. Start Jenkins Service:
bash
Copy code
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
Enable Jenkins to start on boot, start the Jenkins service, and check its status.

4. Configure Jenkins:
Open Jenkins on http://ip:8080
Create a Jenkins agent.
Integrate GitHub with Jenkins under system < configure < find GitHub.
5. Create Jenkins Job:
Name: todo-app
Version Control: Git
GitHub Repo: [Your GitHub Repo]
Branch: develop
Add Build Steps:

sudo docker build . -t todo-app
sudo docker run -d -p 8000:8000 todo-app
6. Run Jenkins Job:
Click on "Build Now" in Jenkins. After a successful build, changes trigger the pipeline automatically.

## Conclusion
Congratulations! You have successfully set up the "TODO-Django-CICD" project locally, on AWS EC2, and with Docker containers. The CI/CD pipeline with Jenkins ensures continuous integration and deployment for an efficient development workflow.


