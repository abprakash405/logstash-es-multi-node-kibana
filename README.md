# logstash-es-multi-node-kibana

-------pre-requisites--------------------------------------------------

apt-get install docker.io -y 

apt-get install jq -y 

#sudo rm /usr/local/bin/docker-compose

VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)

DESTINATION=/usr/local/bin/docker-compose

sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION

sudo chmod 755 $DESTINATION


vi ~/.bashrc

alias dc='docker-compose'

alias d='docker'

source ~/.bashrc


sysctl -w vm.max_map_count=262144


dc up -d 

--------------

install filebeat and set the filebeat.yml as config


curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.2-amd64.deb


sudo dpkg -i filebeat-7.4.2-amd64.deb


vi /etc/filebeat/filebeat.yml 

enabled: true 

--------------

service filebeat start

service filebeat start

#if you want to down the stack and restart follow below steps

dc down 

rm -rf elasticsearch/esdata*/*

dc up -d 
