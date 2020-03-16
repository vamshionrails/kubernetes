# DOCKER
=================

stop:	$systemctl stop docker
start:  $systemctl start docker

docker pull jenkins
docker images
docker ps
docker stop $(docker ps -a -q)

docker run -d -p 9090:8080 -v jenkins_data:/var/jenkins_home --name jenkins003 jenkins/jenkins
docker run -d -p 8090:8080 -v jenkins_data:/var/jenkins_home --name jenkins002 jenkins/jenkins
docker run -d -p 7090:8080 -v jenkins_data:/var/jenkins_home --name jenkins001 jenkins/jenkins

$docker exec -it -u root jenkins002 /bin/bash

$docker stop $(docker ps -a -q)

#docker compose
-----------------------------------
docker-compose up

docker-compose ps -a
        Name            Command   State    Ports
------------------------------------------------
hello-world_my-test_1   /hello    Exit 0   

docker-compose stop

# kubernetes
-----------------


[raptor@raptor ~]$ sudo docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
vamshionrails/centos8   latest              c16b2630cfca        4 minutes ago       221MB
jenkins/jenkins         latest              cf9ba86fd2ce        5 days ago          619MB
haproxy                 latest              ba380812d45c        2 weeks ago         92.5MB
2233466866/centos8      latest              ee017357bf49        4 months ago        220MB
blacklabelops/jenkins   latest              6926b9b79e5d        17 months ago       311MB
[raptor@raptor ~]$ docker^C

create container
-----------------

sudo docker run -d --net=host --dns 8.8.8.8 --name vamshi-centos8 vamshionrails/centos8

[raptor@raptor ~]$ docker container ls
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json: dial unix /var/run/docker.sock: connect: permission denied
[raptor@raptor ~]$ sudo docker container ls
CONTAINER ID        IMAGE                   COMMAND                  CREATED             STATUS              PORTS                               NAMES
aa4e4604e84c        vamshionrails/centos8   "/usr/sbin/init"         10 seconds ago      Up 8 seconds                                            centos8
79335b302f36        jenkins/jenkins         "/sbin/tini -- /usr/…"   26 hours ago        Up 26 hours         50000/tcp, 0.0.0.0:7090->8080/tcp   jenkins004
c06778eff259        jenkins/jenkins         "/sbin/tini -- /usr/…"   26 hours ago        Up 26 hours         50000/tcp, 0.0.0.0:8090->8080/tcp   jenkins002
3ccec267329b        jenkins/jenkins         "/sbin/tini -- /usr/…"   26 hours ago        Up 26 hours         50000/tcp, 0.0.0.0:9090->8080/tcp   jenkins003


login into container
--------------------
sudo docker exec -it -u root centos8 /bin/bash
sudo docker exec -it -u predator centos8 /bin/bash

create image from container
-----------------------------
sudo docker stop vamshi-centos8
sudo docker commit -m "base image" -a "A N other" `sudo docker ps -l -q` vamshi/centos8:v1

sudo docker run -d --net=host --dns 8.8.8.8 --name vamshi-centos8 vamshi/centos8:v1
df9de1e6f6e370d147294a0fdcf3bb3615178b16589f3d278e558239cdc4fff6

sudo docker exec -it -u predator vamshi-centos8 /bin/bash
[predator@raptor /]$ 

docker push to dockerhub
---------------------------
sudo docker login
sudo docker push docker.io/vamshionrails/centos8
sudo docker push docker.io/vamshionrails/centos8:v2

KUBERNETES
----------------------
sudo nano /etc/yum.repos.d/kubernetes.repo

[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg

sudo dnf install -y kubelet kubeadm kubectl --disableexcludes=kubernetes







