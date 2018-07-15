---
layout: post
title: setup gitlab with docker
author: wuwei
date: 2018-07-15
tags:
  - GIT
---
```
docker pull gitlab/gitlab-ce

GITLAB_HOME=`pwd`/data/gitlab
docker run -d \
    --publish 8888:443 --publish 8880:80 --publish 2222:22 \
    --name gitlab \
    --restart always \
    --volume $GITLAB_HOME/config:/etc/gitlab \
    --volume $GITLAB_HOME/logs:/var/log/gitlab \
    --volume $GITLAB_HOME/data:/var/opt/gitlab \
 -e SMTP_ENABLED=true \
 -e SMTP_DOMAIN=163.com \
 -e SMTP_HOST=smtp.163.com \
 -e SMTP_PORT=25 \
 -e SMTP_USER=wuweiwhuict@163.com \
 -e SMTP_PASS=wuwei222 \
 -e SMTP_STARTTLS=false \
 -e SMTP_OPENSSL_VERIFY_MODE=peer \
 -e SMTP_AUTHENTICATION=login \
 -e GITLAB_EMAIL=wuweiwhuict@163.com\
 gitlab/gitlab-ce

 docker exec -t -i gitlab vim /etc/gitlab/gitlab.rb

 external_url "host_ip"

 ```
