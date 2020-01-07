# Docker - Neo4J

> Create directory
```shell
mkdir -p /usr/local/opt/neo4j/3.0
```

> Set permissions on your data folder
```shell
chmod -R ug+w /usr/local/opt/neo4j/
```

> Enable Docker File Sharing (Docker -> Preferences -> '+')
> Start Container
```shell
docker run --restart always -d --name=neo4j3.0 \
-p 7474:7474 \
-p 7687:7687 \
-v /usr/local/opt/neo4j/3.0/data:/data:rw \
-v /usr/local/opt/neo4j/3.0/import:/var/lib/neo4j/import:rw \
-v /usr/local/opt/neo4j/3.0/logs:/logs \
neo4j:3.0
```

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps neo4j3.0
```