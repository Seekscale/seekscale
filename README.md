##### Overall description

Seekscale render farm manager is based on docker, and python celery task queue.
Celery flower (a tool from Celery ecosystem) provides out of the box a web UI and an API
to visualize and launch tasks on your render farm.

##### Prerequisites

On master and node machines, make sure you have docker and docker-compose installed.
We recommand ubuntu server 16.04.

Procedure for ubuntu server 16.04:

sudo apt-get install apt-transport-https
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
apt-cache policy docker-ce
sudo apt-get install -y docker-ce

sudo curl -o /usr/local/bin/docker-compose -L "https://github.com/docker/compose/releases/download/1.15.0/docker-compose-$(uname -s)-$(uname -m)"
sudo chmod +x /usr/local/bin/docker-compose
docker-compose -v


##### Seekscale Master Install

- make sure docker and docker-compose are installed on the host (see the prerequisites)
- cd in master folder
- edit .env file, choose your rabbitMQ credentials, and the version (TAG) of seekscale you want to use
- run "sudo docker-compose up -d"
- run "sudo docker-compose ps" and make sure all containers are online
- with a web browser go on your master ip address and make sure you can see
Celery Flower web UI



##### Seekscale Node Install

- make sure docker and docker-compose are installed on the host (see the prerequisites)
NOTE: if you are not using ubuntu 16.04, the docker executable path might not be
/usr/bin/docker, in that case you need to put the right one in the node docker-compose.yml  "volumes" section (on the left of the :)
- cd in master folder
- edit .env file, put your rabbitMQ credentials, the Seekscale master ip address, and the version (TAG) of seekscale you want to use. This must be the same one than the one you use on the master.
- run "sudo docker-compose up -d"
- run "sudo docker-compose ps" and make sure all containers are online
