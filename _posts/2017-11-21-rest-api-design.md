---
layout: post
title:  "REST API 설계"
crawlertitle: "REST API 설계"
date:   2017-11-21 12:44:54 +0900
categories: posts
tags: ['rest api']
author: youngjae
categories: youngjae
---

#### 응답 방식 
1. only HTTP Status code 
	- 장점: API 표준
	- 단점: 문제에 대한 정보 부족

2. HTTP Status + JSON Body
	- 장점: 문제에 대한 상세 정보 제공
	- 단점: 응답으로 사용되는 JSON 포맷은 오류, 성공에 따라 달라짐
	
3. Forget the HTTP Status (ex: always status 200)
	- 장점: 클라이언트는 응답 Body만 처리하고 Status Code는 무시
	- 단점: RESTful 하지 않음


####