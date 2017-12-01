---
layout: post
cover: 'assets/images/cover4.jpg'
navigation: True
title:  "Git에서 쉘 스크립트 실행 권한 변경 방법"
crawlertitle: "Git에서 쉘 스크립트 실행 권한 변경 방법"
date: 2017-11-30 05:00:00
tags: fables speeches
subclass: 'post tag-content'
log: 'assets/images/ghost.png'
author: youngjae
categories: youngjae
---

작성된 쉘 스크립트를 git push하게 되면 리눅스에서는 기본적으로 아래와 같이 읽기 권한만 가진다.
```
-rw-r--r-- 1 root root   117 Dec  1 07:41 start.sh
```

리눅스에서 실행 권한을 부여하기 위해서는 커밋 전 update-index ----chmod 매개변수를
이용해서 권한을 부여할 수 있다.

```
$ git update-index --chmod=+x startup.sh

$ git update-index --chmod=+x shutdown.sh
```