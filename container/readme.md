

docker exec -u root -ti e826db00b37c /bin/bash

curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.2.3-amd64.deb
sudo dpkg -i elastic-agent-8.2.3-amd64.deb

/etc/init.d/elastic-agent start

----

docker container start -a es-01

docker container start -a kib-01

----

npm install elastic-apm-node --save

-----

https://ubuntu.com/tutorials/running-a-container-with-the-docker-workflow-in-multipass#1-overview

-----

### docker ps

``` https://docs.docker.com/engine/reference/commandline/ps/ ```

#### Show disk usage by container

``` docker ps -s ```

----
publish and expose
 docker run -d --publish=80 busybox top
 docker run -d --expose=8080 busybox top
