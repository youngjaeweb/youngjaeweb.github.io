---
layout: post
cover: 'assets/images/cover4.jpg'
navigation: True
title:  "Windows7에서 Celery Worker 실행 오류 해결 방법"
crawlertitle: "Windows7에서 Celery Worker 실행 오류 해결 방법"
date: 2017-11-22 05:00:00
tags: fables speeches
subclass: 'post tag-content'
log: 'assets/images/ghost.png'
author: youngjae
categories: youngjae
---

아래와 같이 Windows7에서 Celery Worker 실행 오류 발생했다.
구글링 검색 결과 Celery 버전이 문제임을 했다.

공식적으로 Celery 4.0은 Windows를 지원하지 않는다고 한다.
(http://docs.celeryproject.org/en/master/whatsnew-4.0.html#removed-features)

해결은 설치된 4.0.2 버전은 제거를 하고 3.1.25로 설치함으로써 정상적으로 worker가 실행되는 것을 확인했다.
운영 OS와 개발 OS가 다른데 Celery 버전 관리를 어떻게 해야 할지 고민이 필요해 보인다.

<pre>
  {% raw %}
(venv) C:\> celery -A hello.celery worker --loglevel=info
redis://192.168.xxx.xx:6379/0

 -------------- celery@xxxx-xxx-PC v4.0.2 (latentcall)
---- **** -----
--- * ***  * -- Windows-7-6.1.7601-SP1 2017-11-22 17:45:39
-- * - **** ---
- ** ---------- [config]
- ** ---------- .> app:         hello:0x56daf28
- ** ---------- .> transport:   redis://192.168.xxx.xx:6379/0
- ** ---------- .> results:     redis://192.168.xxx.xx:6379/0
- *** --- * --- .> concurrency: 4 (prefork)
-- ******* ---- .> task events: OFF (enable -E to monitor tasks in this worker)
--- ***** -----
 -------------- [queues]
                .> celery           exchange=celery(direct) key=celery


[tasks]


[2017-11-22 17:45:39,351: CRITICAL/MainProcess] Unrecoverable error: AttributeError("Can't pickle local object 'Pool.__init__.&lt;l
ocals&gt;.Process'",)
Traceback (most recent call last):
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\celery\worker\worker.py", line 203, in start
    self.blueprint.start(self)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\celery\bootsteps.py", line 119, in start
    step.start(parent)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\celery\bootsteps.py", line 370, in start
    return self.obj.start()
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\celery\concurrency\base.py", line 131, in start
    self.on_start()
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\celery\concurrency\prefork.py", line 112, in on_start
    **self.options)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\pool.py", line 1008, in __init__
    self._create_worker_process(i)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\pool.py", line 1117, in _create_worker_process

    w.start()
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\process.py", line 122, in start
    self._popen = self._Popen(self)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\context.py", line 383, in _Popen
    return Popen(process_obj)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\popen_spawn_win32.py", line 79, in __init__
    reduction.dump(process_obj, to_child)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\reduction.py", line 99, in dump
    ForkingPickler(file, protocol).dump(obj)
AttributeError: Can't pickle local object 'Pool.__init__.&lt;locals&gt;.Process'
Traceback (most recent call last):
  File "&lt;string&gt;ff",dd line 1, in &lt;module&gt;
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\spawn.py", line 159, in spawn_main
    new_handle = steal_handle(parent_pid, pipe_handle)
  File "d:\study\python\workspace\celerywithflask\venv\lib\site-packages\billiard\reduction.py", line 126, in steal_handle
    _winapi.DUPLICATE_SAME_ACCESS | _winapi.DUPLICATE_CLOSE_SOURCE)
PermissionError: [WinError 5] 액세스가 거부되었습니다
  {% endraw %}
</pre>
