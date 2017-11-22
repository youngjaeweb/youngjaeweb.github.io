---
layout: post
cover: 'assets/images/cover4.jpg'
title:  "Windows 7에 Jekyll 설치하기"
crawlertitle: "Windows 7에 Jekyll 설치하기"
date: 2017-11-20 09:14:54 +0900
subclass: 'post tag-speeches'
logo: 'assets/images/ghost.png'
author: youngjae
categories: youngjae
---

#### 1. Ruby 설치
- https://rubyinstaller.org/downloads/
- Ruby 2.3.3 (x64) 다운로드 후 설치(Setup에서 PATH 추가 옵션 선택)

#### 2. Development kit 설치
- https://rubyinstaller.org/downloads/
- DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe 다운로드 후 설치(설치 경로 설정 필요)
~~~
C:\> cd C:\RubyDevKit
C:\> ruby dk.rb init
~~~
- config.yml에 Ruby Path 추가 후 
~~~
C:\> ruby dk.rb install
~~~

#### 3. Bundler와 Jekyll 설치

~~~
C:\> gem install bundler
C:\> gem install jekyll
~~~

- 설치 중 SSL 인증서 체킹 오류 발생 할 경우에 해결 방법
~~~
파일위치 - %userprofile%\.gemrc
:ssl_verify_mod: 0
~~~



#### 4. Jekyll Serve를 위한 필수 Gem 설치
~~~
C:\> gem install rouge
C:\> gem install minima
C:\> gem install jekyll-feed
C:\> gem install tzinfo-data
~~~

#### 5. 프로젝트 생성 및 실행
~~~
C:\> jekyll new new-blog
C:\> cd new-blog
C:\> bundle exec jekyll serve
~~~

- Serve 중 오류가 발생 할 경우 필요한 Gem이 설치가 안되었을 경우 추가로 설치


##### 참고 

- Gem install directory 설정
~~~
gem install jekyll -n /usr/local/bin
~~~
- Gem install 버전 설정 
~~~
gem install jekyll -v 
~~~
- 설치된 모든 Gem uninstall
~~~
gem uninstall -aIx
~~~