# kubernetes

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

sudo docker run -d --net=host --dns 8.8.8.8 --name centos8 vamshionrails/centos8
aa4e4604e84cc8705140cac077a09f2a9c75662337df7ea24ea39fa82c3a7831
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