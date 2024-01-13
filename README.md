#TODO-Django-CICD

##Introduction:

This README provides a comprehensive guide to set up and run the "TODO-Django-CICD" project locally, on AWS EC2, and using Docker containers. The project is a Django-based TODO application integrated with Continuous Integration and Continuous Deployment (CI/CD) pipelines for streamlined development workflows.

##Pre-requisites:
Before you begin, ensure you have the following prerequisites installed:

1. Git
2. Python (with virtualenv)
3. Docker
4. Jenkins
5. Access to AWS EC2 instance
6. Local Setup (VS Code)

```
git clone https://github.com/Akashdhengale/django-todo-cicd.git
```

###Setup Python Virtual Environment:
```
pip install virtualenv
```
```
python -m venv env
```
### TO Activate Vitual Environment:

```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\env\Scripts\activate
```
```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Default
```
```
pip install django
```

Then Run below commands to run the code:

python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
Create Requirement.txt:


pip freeze > requirements.txt
AWS EC2 Setup
SSH into Server:


ssh into server
mkdir project
cd project
git clone https://github.com/LondheShubham153/django-todo-cicd.git
Install Dependencies:


sudo apt install python3-pip
sudo apt-get update
pip3 install django
Run Django Commands:


python3 manage.py runserver 0.0.0.0:8000
python manage.py migrate
Docker Container Setup
Kill Process on Port 8000:


lsof -i:8000
kill -9 pid
Install Docker:


sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
Install Docker Components:


sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Build Docker Image:


sudo docker build . -t todo-app
Run Docker Container:


sudo docker run -d -p 8000:8000 todo-app
Continuous Integration and Deployment (CI/CD) Pipeline with Jenkins
Install Jenkins:


sudo apt update && sudo apt upgrade -y
sudo apt install default-jre -y && sudo apt install default-jdk -y
Install Jenkins on Ubuntu 20.04:


curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
Start Jenkins Service:


sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
Configure Jenkins:

Open Jenkins on http://ip:8080
Create a Jenkins agent.
Integrate GitHub with Jenkins under system < configure < find GitHub.
Create Jenkins Job:

Name: todo-app
Version Control: Git
GitHub Repo: [https://github.com/Akashdhengale/django-todo-cicd]
Branch: develop
Add Build Steps:

sudo docker build . -t todo-app
sudo docker run -d -p 8000:8000 todo-app
Run Jenkins Job:

Click on "Build Now" in Jenkins. After a successful build, changes trigger the pipeline automatically.

## Conclusion
Congratulations! You have successfully set up the "TODO-Django-CICD" project locally, on AWS EC2, and with Docker containers. The CI/CD pipeline with Jenkins ensures continuous integration and deployment for efficient development.


