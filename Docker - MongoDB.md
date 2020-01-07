# Docker - MongoDB


> Create directory
```shell
mkdir -p /usr/local/opt/mongo/3.0
```

> Set permissions on your data folder
```shell
chmod -R ug+w /usr/local/opt/mongo/
```

> Enable Docker File Sharing (Docker -> Preferences -> '+')
> Start Container
```shell
docker run --restart always -d --name=mongo4.0 \
-p 27017:27017 \
-v /usr/local/opt/mongo:/data/db \
mongo:4.0
```

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps mongo4.0
```