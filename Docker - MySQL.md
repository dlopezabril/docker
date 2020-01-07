# Docker - MySQL


> Create directory
```shell
mkdir -p /usr/local/opt/mysql/5.7
```

> Set permissions on your data folder
```shell
chmod -R ug+w /usr/local/opt/mysql/
```

> Enable Docker File Sharing (Docker -> Preferences -> '+')
> Start Container
```shell
docker run --restart always -d --name mysql5.7 \
-v /usr/local/opt/mysql/5.7:/var/lib/mysql \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
mysql:5.7
```

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps mysql5.7
```

> Backup
```shell
$ docker exec mysql5.7 sh -c 'exec mysqldump --all-databases -uroot -p"mysecretpassword"' > ~/Desktop/db.sql
```

> Restore
```shell
$ docker exec -i mysql5.7 sh -c 'exec mysql -uroot -p"mysecretpassword"' < ~/Desktop/db.sql
```

!!! note Links
[How to Run MySQL in a Docker Container](https://medium.com/@crmcmullen/how-to-run-mysql-in-a-docker-container-on-macos-with-persistent-local-data-58b89aec496a)
!!!