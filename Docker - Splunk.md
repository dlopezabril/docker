# Docker - Splunk


# Enable Docker File Sharing (Docker -> Preferences -> '+')
docker run -d --name splunk \
-p 8000:8000 \
-e "SPLUNK_START_ARGS=--accept-license" \
-e "SPLUNK_PASSWORD=mysecretpassword" \
splunk/splunk:7.3.3

# Start Splunk
docker run -d -p 8000:8000 -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=mysecretpassword" --name splunk splunk/splunk:7.3.3

admin - mysecretpassword
http://localhost:8000/

# Tail logs
docker logs --tail 5 --follow --timestamps splunk

Install App:   Apps → Manage Apps → Browse more apps
Configuration: Settings → (SYSTEM) Server Settings
Licensing:     Settings → (SYSTEM) Licensing
Sourcetype:    Settings → (DATA) Source types
Eventgenerator:

# https://github.com/splunk/eventgen