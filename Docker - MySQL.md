# Docker - MySQL


# Create directory
mkdir -p ~/containers/mysql

# Start Container
docker run --restart always -d --name mysql5.7 \
-v ~/containers/mysql:/var/lib/mysql \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
mysql:5.7

# Tail logs
docker logs --tail 5 --follow --timestamps mysql5.7

# Backup
docker exec mysql5.7 sh -c 'exec mysqldump --all-databases -uroot -p"mysecretpassword"' > ~/Desktop/db.sql

# Restore
docker exec -i mysql5.7 sh -c 'exec mysql -uroot -p"mysecretpassword"' < ~/Desktop/db.sql

# https://medium.com/@crmcmullen/how-to-run-mysql-in-a-docker-container-on-macos-with-persistent-local-data-58b89aec496a
