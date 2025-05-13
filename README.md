
# Run n8n docker
## Create volume
docker volume create n8n_data

## Run container
docker run -it --rm --name n8n_with_docker -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n

# Run n8n_whih_docker

## Create volume
docker volume create n8n_data

## Build image
cd n8n_with_docker
docker image build -t n8n_with_docker .

## Run container
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n -v /var/run/docker.sock:/var/run/docker.sock n8n_with_docker
docker run -it --rm --name n8n

## Grant group access to docker service
docker exec --user root -it n8n chown root:docker /var/run/docker.sock
docker exec --user root -it n8n chmod g+w /var/run/docker.sock
docker exec --user root -it n8n ls -lrt /var/run/docker.sock


## Run docker-compose

docker-compose -f docker-compose.n8n.yml build
docker-compose -f docker-compose.n8n.yml up -d


# URL

http://localhost:5678

