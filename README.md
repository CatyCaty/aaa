# OpenShift_LearningPath

https://console.redhat.com/allservices

https://github.com/cloudacademy/openshift-voteapp-demo

https://github.com/redhat-developer

Openshift PaaS

OpenShift Origin
OpenShift Online
OpenShift Dedicated Managed private cluster on AWS/ Google Clouds /Azure
OpenShift Enterprise On-Premise private PaaS

OpenShift Origin - basiert auf docker und kubernetes, cluster manager, mit einigen Entwicklertools DevOps-Tools, schnelle Entwicklung Deployment, lifecycle management.

Source Code Management - Github
Pipelines - develop, build, test, deploy
Registry - verwaltet Docker images
Software defined network - networking capabilities out of the box

https://console.redhat.com/openshift/sandbox
oc login -u user1
oc new-project microservice
oc new-app https://github.com/sclorg/cakephp-ex

oc get pods -o wide
NAME                          READY   STATUS      RESTARTS   AGE     IP             NODE                 NOMINATED NODE   READINESS GATES
cakephp-ex-1-build            0/1     Completed   0          2m18s   10.217.0.141   crc-ksq4m-master-0   <none>           <none>
cakephp-ex-787d4788fb-4lc7h   0/1     Pending     0          76s     <none>         <none>               <none>           <none>

oc logs cakephp-ex-787d4788fb-4lc7h
oc logs cakephp-ex-1-build

oc project --- Using project "crt-redhatdevrob-dev" from context named "crt-redhatdevrob-context" on server "https://172.30.0.1:443".

oc whoami

oc status

oc api-resources

oc help

oc create --help

oc explain pods

oc get user
oc get identity
oc get groups
oc adm groups new devops developer kubeadmin
oc adm groups remove-users devops developer kubeadmin
NAME     USERS
devops   developer, kubeadmin

oc describe user
oc describe group
oc delete user frank

oc delete identity ....
oc logout

!oc completion bash > oc_bash_completion
oc edit project microservice
"cluster entry
oc config view

oc whoami -c
microservice/api-crc-testing:6443/kubeadmin

oc status

#gather debug information from a pod
oc adm must-gather

oc adm new-project myproject
oc edit project microservice
oc adm node-logs --role master -u kubelet
oc adm pod-network isolate-projects
oc adm pod-network isolate-projects microservice
oc image mirror registry.access.redhat.com/ubi8/ubi:latest=default-route-openshift-image-registry.apps-crc.testing/demo/ubi8:latest --insecure=true --filter-by-os=linux/amd64

#cluster operators kubeadmin
oc get co
What is odo?

#Docker
<!DOCTYPE html>
<html>
<head>
    <title>Meine Docker-Seite</title>
</head>
<body>
    <h1>Willkommen auf meiner Docker-Seite!</h1>
</body>
</html>


#Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

docker build -t my-docker-page .


#docker-compose.yml
version: '3'
services:
  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: my_database
      MYSQL_USER: my_user
      MYSQL_PASSWORD: my_password
  backend:
    build: ./backend
    restart: always
    ports:
      - "3000:3000"
    depends_on:
      - db

#
docker volume create mysql_data

#
docker run -d -p 3306:3306 -v mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root_password mysql:5.7


#
https://github.com/docker/multi-container-app
git clone https://github.com/docker/multi-container-app
docker compose up -d
http://localhost:3000/
docker compose watch
delete
#
git clone https://github.com/docker/multi-container-app
todo-database:
    # ...
    volumes:
      - database:/data/db
                      
# ...
volumes:
  database:

#
git clone https://github.com/docker/bindmount-apps
todo-app:
    # ...
    volumes:
      - ./app:/usr/src/app
      - /usr/src/app/node_modules
docker compose up -d
localhost:3001

#publish your image
rename the image
docker tag docker/docker-dotnet-sample-server robixondocker/docker-dotnet-sample-server
docker push robixondocker/docker-dotnet-sample-server

#publish 
docker run -it --rm -p 8000:8080 --name aspnetcore_sample mcr.microsoft.com/dotnet/samples:aspnetapp
docker tag mcr.microsoft.com/dotnet/samples robixondocker/mcr.microsoft.com/dotnet/sample

#openshift
git clone https://github.com/docker/multi-container-app











  











