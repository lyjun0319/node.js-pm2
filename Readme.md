# AWS Node.js Setting Guide

#### 1. AWS Server ubuntu 인스턴스
#### 2. ubuntu 접속
```text
$ ssh -i "pemkey" 아이디@아이피.ap-northeast-2.compute.amazonaws.com
```
#### 3. 서버 업데이트
```text
$ sudo apt-get update
```

#### 4. 노드설치
``` text
# Using Ubuntu version
$ curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```