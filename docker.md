docker pull
-----------

docker pull archlinux/base
sudo docker run -it --rm archlinux/base

commit
------
docker commit -m "arch base image" ecstatic_chaum vamshionrails/archlinux_base

jenkins
-------------
docker pull vamshionrails/jenkins
docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts