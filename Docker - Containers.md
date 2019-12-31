# Docker - Containers

!!! note MYSQL

> [How to Run MySQL in a Docker Container](https://medium.com/@crmcmullen/how-to-run-mysql-in-a-docker-container-on-macos-with-persistent-local-data-58b89aec496a)
> **Create Docker:**
```shell
# Create directory
mkdir -p /usr/local/opt/mysql/5.7

# Set permissions on your data folder
chmod -R ug+w /usr/local/opt/mysql/

# Enable Docker File Sharing For Your Data Folder
# Docker -> Preferences -> '+'

# Start MYSQL Container
docker run --restart always -d --name mysql5.7 \
-v /usr/local/opt/mysql/5.7:/var/lib/mysql \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
mysql:5.7

# Tail logs MYSQL Container
docker logs --tail 5 --follow --timestamps mysql5.7
```

> **Backup and Restore:**
```shell
# Backup MYSQL
$ docker exec mysql5.7 sh -c 'exec mysqldump --all-databases -uroot -p"mysecretpassword"' > ~/Desktop/db.sql

# Restore MYSQL
$ docker exec -i mysql5.7 sh -c 'exec mysql -uroot -p"mysecretpassword"' < ~/Desktop/db.sql
```
!!!

!!! note Neo4J

> **Create Docker:**
```shell
# Create directory
mkdir -p /usr/local/opt/neo4j/3.0

# Set permissions on your data folder
chmod -R ug+w /usr/local/opt/neo4j/

# Enable Docker File Sharing For Your Data Folder
# Docker -> Preferences -> '+'

# Start Neo4J Container
docker run --restart always -d --name=neo4j3.0 \
-p 7474:7474 \
-p 7687:7687 \
-v /usr/local/opt/neo4j/3.0/data:/data:rw \
-v /usr/local/opt/neo4j/3.0/import:/var/lib/neo4j/import:rw \
-v /usr/local/opt/neo4j/3.0/logs:/logs \
neo4j:3.0

# Tail logs Neo4J Container
docker logs --tail 5 --follow --timestamps neo4j3.0
```
!!!

!!! note MongoDB
> **Create Docker:**

```shell
# Create directory
mkdir -p /usr/local/opt/mongo/3.0

# Set permissions on your data folder
chmod -R ug+w /usr/local/opt/mongo/

# Enable Docker File Sharing For Your Data Folder
# Docker -> Preferences -> '+'

# Start MongoDB Container
docker run --restart always -d --name=mongo4.0 \
-p 27017:27017 \
-v /usr/local/opt/mongo:/data/db \
mongo:4.0

# Tail logs MongoDB Container
docker logs --tail 5 --follow --timestamps mongo4.0
```
!!!

!!! note Gitlab
[A step-by-step guide to running GitLab CE in Docker - IBM Code](https://developer.ibm.com/code/2017/07/13/step-step-guide-running-gitlab-ce-docker/)
> **Create Docker:**
```shell
# Create directory
mkdir -p /usr/local/opt/gitlab

# Set permissions on your data folder
chmod -R ug+w /usr/local/opt/gitlab/

# Enable Docker File Sharing For Your Data Folder
# Docker -> Preferences -> '+'

# Add line in host (sudo nano /etc/hosts)
# 127.0.0.1       gitlab.local

# Start Gitlab Container Last Version
docker run --detach \
  --hostname gitlab.local \
  --publish 30080:30080 \
  --publish 30022:22 \
  --name gitlab \
  --restart always \
  --volume /usr/local/opt/gitlab/config:/etc/gitlab \
  --volume /usr/local/opt/gitlab/logs:/var/log/gitlab \
  --volume /usr/local/opt/gitlab/data:/var/opt/gitlab \
  --env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.local:30080'; gitlab_rails['gitlab_shell_ssh_port']=30022;" \
  gitlab/gitlab-ce:latest


# Start Gitlab Container Version 9.1.0-ce.0
docker run --detach --name gitlab \
	--hostname gitlab.example.com \
	--publish 30080:30080 \
         --publish 30022:22 \
	--env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.example.com:30080'; gitlab_rails['gitlab_shell_ssh_port']=30022;" \
	gitlab/gitlab-ce:9.1.0-ce.0
  
  
# 4 minutes later...
# http://gitlab.local:30080
  
# Tail logs gitlab Container
docker logs --tail 5 --follow --timestamps gitlab
```