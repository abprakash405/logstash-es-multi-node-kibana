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

vi docker-compose.yml 
mkdir elasticsearch 
cd elasticsearch
chmod 777 -R *
cd .. 

dc up -d 

mkdir logstash 
mkdir logstash/config 
chmod 777 -R logstash/* 




dc down 
rm -rf elasticsearch/esdata*/*
dc up -d 
