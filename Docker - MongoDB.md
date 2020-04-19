# Docker - MongoDB


# Create directory
mkdir -p ~/Desktop/mongo

# Start Container
docker run --restart always -d --name=mongo4.0 \
-p 27017:27017 \
-v ~/Desktop/mongo:/data/db \
mongo:4.0

# Tail logs
docker logs --tail 5 --follow --timestamps mongo4.0
