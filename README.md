# monstack

start grafana with datasources and dashboards already provisioned, prometheus, alertmanager, loki, promtail, flog and nginx as reverse proxy with a single docker composer file

# disclaimer

this is for development or evaluation purpose only!

THIS IS NOT PRODUCTION READY

# system requirements
1. this is only tested on EL9 aka centos stream 9
2. docker-ce or another docker compatible container runtime installed
3. docker-compose installed

# usage
1. clone repo
```
git clone git@github.com:iamarno/monstack-eval.git
```
2. create data directories
```
cd monstack-eval && mkdir prometheus_data grafana_data
```
3. replace UID in `docker-compose.yaml` with the UID of the user executing `docker-compose up` (next step).
show your uid by entering `echo $UID` into the terminal
```
user: '1000' <- replace with your user UID
```
4. start the containers
```
docker-compose up
```
5. visit the grafana login page
```
http://yourserverip/login
```
6. login with default user admin / admin


# additional information

show prometheus gui
```
http://yourserverip:9090
```
show alertmanager gui
```
http://yourserverip:9093
```

send test alert to alertmanager (from localhost)
```
curl -H 'Content-Type: application/json' -d '[{"labels":{"alertname":"testalert"}}]' http://localhost:9093/api/v1/alerts
```

setup telegram bot in `alertmanager.yml` to recieve alerts via telegram
```
bot_token: 1234561111111111222222222233333333334444444444 # insert your bot_token here
chat_id: -123456789 # insert your chat_id here
```
