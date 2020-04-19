# Docker - Neo4J


# Create directory
mkdir -p ~/Desktop/neo4j

# Start Container
docker run --restart always -d --name=neo4j3.0 \
-p 7474:7474 \
-p 7687:7687 \
-v ~/Desktop/neo4j/data:/data:rw \
-v ~/Desktop/neo4j/import:/var/lib/neo4j/import:rw \
-v ~/Desktop/neo4j/logs:/logs \
neo4j:3.0

# Tail logs
docker logs --tail 5 --follow --timestamps neo4j3.0
