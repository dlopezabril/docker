# Docker - Gitlab


# Create directory
mkdir -p ~/Desktop/mysql

# Start Container
docker run --detach \
  --hostname gitlab.local \
  --publish 30080:30080 \
  --publish 30022:22 \
  --name gitlab \
  --restart always \
  --volume ~/Desktop/gitlab/config:/etc/gitlab \
  --volume ~/Desktop/gitlab/logs:/var/log/gitlab \
  --volume ~/Desktop/gitlab/data:/var/opt/gitlab \
  --env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.local:30080'; gitlab_rails['gitlab_shell_ssh_port']=30022;" \
  gitlab/gitlab-ce:latest

# Start Container
docker run --detach --name gitlab \
	--hostname gitlab.example.com \
	--publish 30080:30080 \
         --publish 30022:22 \
	--env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.example.com:30080'; gitlab_rails['gitlab_shell_ssh_port']=30022;" \
	gitlab/gitlab-ce:9.1.0-ce.0

# 4 minutes later... http://gitlab.local:30080

# Tail logs
docker logs --tail 5 --follow --timestamps gitlab
