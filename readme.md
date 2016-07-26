## Introduction
This is a docker-compose file to build Graylog 2

## Git repository
The source files for this project can be found here: https://github.com/taladocker/graylog

## Installation

```
cd /opt
git clone {graylog-git-repo}
groupadd -g 1100 graylog
useradd -g 1100 -u 1100 graylog
chown -R graylog:graylog /opt/graylog
cd graylog
```

Create new docker-compose config *docker-compose.prod.yml*

```
graylog:
  environment:
    GRAYLOG_PASSWORD_SECRET: password
    GRAYLOG_ROOT_PASSWORD_SHA2: password-sha2
    GRAYLOG_REST_TRANSPORT_URI: http://ip-address:12900
```

**Note**: password-sha2 is generated with `echo -n yourpassword | shasum -a 256`

Start service by run the following

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

## Plugins

### Slack

```
docker exec -it graylog-server bash -c "cd /usr/share/graylog/plugin; wget https://github.com/Graylog2/graylog-plugin-slack/releases/download/2.2.1/graylog-plugin-slack-2.2.1.jar"
```