# Docker - Splunk

> Create directory
```shell
mkdir -p /usr/local/opt/splunk/7.3.3
```

> Set permissions on your data folder
```shell
chmod -R ug+w /usr/local/opt/splunk/
```

> Enable Docker File Sharing (Docker -> Preferences -> '+')
> Start Container
```shell
docker run -d --name splunk \
-p 8000:8000 \
-e "SPLUNK_START_ARGS=--accept-license" \
-e "SPLUNK_PASSWORD=mysecretpassword" \
-v /usr/local/opt/splunk/7.3.3/etc:/opt/splunk/etc \
-v /usr/local/opt/splunk/7.3.3/var:/opt/splunk/var \
splunk/splunk:7.3.3
```

4 minutes later... http://gitlab.local:30080

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps gitlab
```