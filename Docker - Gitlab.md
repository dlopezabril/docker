# Docker - Gitlab

> Create directory
```shell
mkdir -p /usr/local/opt/gitlab
```

> Set permissions on your data folder
```shell
chmod -R ug+w /usr/local/opt/gitlab/
```

> Enable Docker File Sharing (Docker -> Preferences -> '+')
> Start Container
```shell
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
```

> Start Container
```shell
docker run --detach --name gitlab \
	--hostname gitlab.example.com \
	--publish 30080:30080 \
         --publish 30022:22 \
	--env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.example.com:30080'; gitlab_rails['gitlab_shell_ssh_port']=30022;" \
	gitlab/gitlab-ce:9.1.0-ce.0
```

4 minutes later... http://gitlab.local:30080

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps gitlab
```