# Docker - MySQL


# Create directory
mkdir -p ~/containers/mysql

# Start Container

# CENTOS
docker run --restart always -d --name mysql5.7 \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
mysql:5.7

# UBUNTU
docker run --restart always -d --name mysql5.7 \
-v ~/containers/mysql:/var/lib/mysql:rw \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
mysql:5.7


# Tail logs
docker logs --tail 100 --follow --timestamps mysql5.7

# Backup
docker exec mysql5.7 sh -c 'exec mysqldump --all-databases -uroot -p"mysecretpassword"' > ~/Desktop/database.sql

# Restore (previously to create database in mysql)
docker exec -i mysql5.7 sh -c 'exec mysql -uroot -p"mysecretpassword" --database="example"' < ~/Desktop/database.sql

# https://medium.com/@crmcmullen/how-to-run-mysql-in-a-docker-container-on-macos-with-persistent-local-data-58b89aec496a
