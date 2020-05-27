# Docker - System Commands


# Stop all images
docker container stop $(docker container ps -a -q)

# Remove all containers
docker container rm $(docker container ps -a -q)

# Delete all images
docker rmi $(docker images -a -q)

# Get container IP
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_id

# List
watch docker ps -a