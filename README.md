FROM nginx:alpine
COPY ./src /usr/share/nginx/html
7\)
Name: mavenweb-server

AMI: Ubuntu 22.04 (Free tier)

Instance Type: t2.micro

Key Pair: Create/download .pem

Security Group:

Allow SSH (22)

Allow HTTP (80)

Allow Custom TCP 8080

Allow Custom TCP 3000 (if needed)

Allow Custom TCP 8081 (for Nagios)

Leave everything else default → Launch.



Click your instance → Connect → EC2 Instance Connect → Connect.




commands in aws-


sudo su

sudo apt-get update

sudo apt-get install docker.io
sudo apt intall git
sudo apt install nano

git clone http of maven-web application

-navigate to maven-web application 
ls
cd maven-web folder name

ls

nano DockerFile



sudo docker built -t mywebapp .

sudo docker run -d -p 80:80 mywebapp

then go to chrome incognito and paste go into details and paste auto assigned ip address in incognito with port no 

ex 3.231.271.190:8080




welcome to maven web! in local host
sudo docker ps
sudo docker stop [id]


-----------------------------------------------------------------------------------
FROM node:16-alpine
WORKDIR /app
COPY calculator.js /app
CMD ["node", "calculator.js"]


FROM nginx:alpine
COPY . /usr/share/nginx/html
----------------------------------------------------------------------------------
Docker power shell calc
docker build -t simple-calc
docker run simple-calc
docker ps
docker login
docker tag simple-calc [dockerusername]/simple-calc
docker push [dockerusername]/simple-calc

(del img)
docker ps -a
docker rm [container_id]
docker rmi [dockerusername]/simple-calc

(again pull from docker hub)
docker pull [dockerusername]/simple-calc
docker run [dockerusername]/simple-calc

(again del)
docker rm [container_id]
docker rmi [dockerusername]/simple-calc

docker logout
----------------------------------------------------------------------------------

\- minikube start

kubectl create deployment mynginx --image=nginx

kubectl get deployments

--u should see nginx

kubectl get pods 

//expose deployment service

kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80 -- for default like nginx

kubectl expose deployment mynginx --type=NodePort --port=8080 --target-port=8080 -- for customade images



kubectl port-forward svc/mynginx 80:80 - for nginx 

now go to chrome and paste localhost:80 - for nginx 

and localhost:8080 - for other images




kubectl scale deployment mynginx --replicas=4

---------------------------------------------------------------------
minikube start --driver=docker

kubectl create deployment mynginx --image=nginx

kubectl get deployments

kubectl get pods

kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80

kubectl get svc

minikube service mynginx

kubectl port-forward svc/mynginx 8081:80 

kubectl scale deployment mynginx --replicas=4

kubectl get pods

kubectl port-forward svc/mynginx 8081:80 

kubectl delete deployment mynginx

kubectl delete svc mynginx


--------------------------------------------------------------------------
pipeline {
    agent any
    tools{
        maven 'maven3'
    }
    stages {
        stage('git repo & clean') {
            steps {
                 bat """if exist myjavaapp (
                        rmdir /s /q myjavaapp
                      )"""
                //bat "rmdir  /s /q mavenjava"
                bat "git clone https://github.com/adityapanyala/myjavaapp.git"
                bat "mvn clean -f myjavaapp"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f myjavaapp" 
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f myjavaapp"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f myjavaapp"
            }
        }
    }
}
--------------------------------------------------------------------------

ngrok - tunnelling

----

webhooks

install ngrok

sign up ngrok

open the cmd prompt of ngrok




>ngrok http 80


GitHub--repo--settiings--webhoooks-underpayload-paste grok forwarding url



add - /github-webhook/ 

https://9938c896b282.ngrok-free.app/github-webhook/
       

&nbsp;      v
from ngrok http 80 running in ngrok application in downloads C:/



----------------------------------------------------
ngios- 

1)docker pull jasonrivers/nagios:latest
docker run --name nagiosdemo -p 3000:80 jasonrivers/nagios:latest
//docker run -d -p 3000:80 jasonrivers/nagios

open localhost:3000 in browser

username- nagiosadmin
ps- nagios
login to nagios dashboard



//docker pull jasonrbriggs/nagios
----------------------------------------------------------------
DONEEEEEEEEEEEEEEE


https://chatgpt.com/share/691fd04c-1cdc-8000-815b-487af0d79d95
