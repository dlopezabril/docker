# Docker - MySQL


# Create directory
mkdir -p ~/containers/postgres

# Start Container
docker run --restart always -d --name=postgres12 \
-e POSTGRES_PASSWORD=mysecretpassword \
-p 5432:5432 \
-v $HOME/Desktop/postgres:/var/lib/postgresql/data \
postgres:12

# Tail logs
docker logs --tail 100 --follow --timestamps postgres12

# Backup
docker exec -t postgres12 pg_dumpall -c -U postgres > ~/Desktop/dump`date +%d-%m-%Y"_"%H_%M_%S`.sql

# Restore (previously to create database in mysql)
cat your_dump.sql | docker exec -i postgres12 psql -U postgres
