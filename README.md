## Install and run ##
    
    Forbuild docker image:
    sudo docker build --tag netcat-alpine .

    Create bridge network:
    sudo docker network create hw-network

    Run server container
    sudo docker run -d --name server-container --network hw-network -v "$(pwd)":/scripts netcat-alpine /scripts/server.sh

    Run client container:
    sudo docker run --name client-container --network hw-network -v "$(pwd)":/scripts netcat-alpine /scripts/client.sh

    Commands to verify containers connectivity between container:
    sudo docker run --rm --network hw-network netcat-alpine ping -c 3 server-container

    Commands to verify netcat scripts:
    sudo docker logs server-container
