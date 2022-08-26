

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
