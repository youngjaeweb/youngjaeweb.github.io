---
layout: post
cover: 'assets/images/cover3.jpg'
naviation: True
title:  "Redis 설치 및 원격 접속 허용 방법"
crawlertitle: "Redis 설치 및 원격 접속 허용 방법"
date:   2017-11-22 12:44:54 +0900
tags: redis
subclass: 'post'
author: youngjae
categories: youngjae
---

### 1. Docker Container 기동
- Fedora Image

### 2. Redis 설치

```
$ yum clean all;yum install redis
```

### 3. 원격 접속 허용을 위한 설정
>/etc/redis.conf
- bind 127.0.0.1 -> bind 0.0.0.0
- protected-mode yes -> no

### 4. Redis 실행(Daemon mode)
~~~
$ redis-server /etc/redis.conf --daemonize yes
~~~
