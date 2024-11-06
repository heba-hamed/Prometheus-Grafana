In linux :
firstly, create directory:  
      mkdir prometheus
      cd prometheus/
secondly, create a compose yml file inside directory:
      vim docker-compose.yml
then run these commands:
      docker-compose up -d
      docker ps   # to certain the container is created and started successfully
then create a yml file:
      vim prometheus.yml
then run these commands: 
      docker run -d --name prometheus -p 9090:9090 --mount type=bind,source=$PWD/prometheus.yml,target=/etc/prometheus/prometheus.yml --network prometheus_default prom/prometheus
      docker ps   # to certain the container is created successfully
then create new volume y running command:
      docker volume create grafana
then run this command:
       docker run -d --name grafana --volume grafana:/var/lib/grafana -p 3000:3000 --network prometheus_default  grafana/grafana
finally, in browser write:
      your local ip:9100  # to start page of node-exporter
      your local ip:9090  # to start page of prometheus
      your local ip:3000  # to start page of grafana
      
