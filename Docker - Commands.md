# Docker - System Commands

> Start Docker App
```shell
open -n /Applications/Docker.app
```
> Stop all images
```shell
docker stop $(docker ps -a -q)
```

> Remove all containers
```shell
docker rm $(docker ps -a -q)
```
> Delete all images
```shell
docker rmi $(docker images -a -q)
```
> Get container IP
```shell
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_id
```