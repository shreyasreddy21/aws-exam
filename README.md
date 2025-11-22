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

sudo docker --version

sudo docker images

sudo docker ps

git clone http of maven-web application

-navigate to maven-web application 

cd maven-web folder name

ls

nano DockerFile



sudo docker built -t img1 .




sudo docker images

sudo docker run -d -p 8080:8080 img1

then go to chrome incognito and paste go into details and paste auto assigned ip address in incognito with port no 

ex 3.231.271.190:8080




welcome to maven web! in local host



-----------------------------------------------------------------------------------
Q ) kuberenetes - minikube

pre req- docker desktop and docker image



Minikube cmds- 





minkube start

minikube status

kubectl get deployments

--if u have previous deployments so to delete

kubectl delete deployment dep\_name

kubectl get pods

-- to delete the pods 

kubectl delete pod pod\_name

-- to create deployment 

kubectl create deployment mynginx --image=<docker hub image name>

eg: kubectl create deployment mynginx --image=<imagename>

-go to docker hub

-go to repo

-click on public view

-image name 

--------

\- default image present in docker is nginx

kubectl create deployment mynginx --image=nginx

kubectl get deployments

--u should see nginx

kubectl get pods 

kubectl describe pods 

//expose deployment service

kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80 -- for default like nginx

kubectl expose deployment mynginx --type=NodePort --port=8080 --target-port=8080 -- for customade images

kubectl get service mynginx 

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

kubectl scale deployment mynginx --replicas=4
kubectl get pods

kubectl delete deployment mynginx
kubectl delete svc mynginx


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

1)

docker run -d -p 3000:80 jasonrivers/nagios

open localhost:3000 in browser

username- nagiosadmin
ps- nagios
login to nagios dashboard



//docker pull jasonrbriggs/nagios
----------------------------------------------------------------
DONEEEEEEEEEEEEEEE


https://chatgpt.com/share/691fd04c-1cdc-8000-815b-487af0d79d95
