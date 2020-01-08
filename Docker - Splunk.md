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
```shell
docker run -d --name splunk \
-p 8000:8000 \
-e "SPLUNK_START_ARGS=--accept-license" \
-e "SPLUNK_PASSWORD=mysecretpassword" \
splunk/splunk:7.3.3
```
```shell
docker run -d -p 8000:8000 -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=mysecretpassword" --name splunk splunk/splunk:7.3.3
```
```shell
open -n /Applications/Google\ Chrome.app/
```

admin - mysecretpassword
http://localhost:8000/

> Tail logs
```shell
docker logs --tail 5 --follow --timestamps splunk
```

Install App:   Apps → Manage Apps → Browse more apps
Configuration: Settings → (SYSTEM) Server Settings
Licensing:     Settings → (SYSTEM) Licensing
Sourcetype:    Settings → (DATA) Source types
Eventgenerator:

[GitHub - splunk/eventgen: Splunk Event Generator: Eventgen](https://github.com/splunk/eventgen)