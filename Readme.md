# AWS Node.js Setting Guide

#### AWS Server ubuntu 인스턴스
#### ubuntu 접속
```text
$ ssh -i "pemkey" 아이디@아이피.ap-northeast-2.compute.amazonaws.com
```
#### 서버 업데이트
```text
$ sudo apt-get update
```

#### 노드설치
``` text
# Using Ubuntu version
$ curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```

#### NPM 설치
```text
$ sudo npm install -g npm
```

#### express 설치
```text
$ sudo npm install -g express
```

#### 프로젝트 폴더 생성
```text
$ sudo mkdir "파일명"
```

#### 프로젝트 폴더 권한 변경 생성
```text
$ sudo chown "아이디" -
```

#### 폴더 node 초기화
```text
$ npm init
```

#### express 설치
```text
$ npm install --save express
```
#### app.js 생성
```text
$ vi app.js
```

#### app.js 수정
```javascript
const http = require('http');
const fs = require('fs');

const app = http.createServer(function(request,response){
    var url = request.url;
    if(request.url == '/'){
      url = '/index.html';
    }
    if(request.url == '/favicon.ico'){
      response.writeHead(404);
      response.end();
      return;
    }
    response.writeHead(200);
    response.end(fs.readFileSync(__dirname + url));
 
});
app.listen(8080);
```

#### AWS 인스턴스 보안그룹 8080 port 개방

#### PM2 설치
```text
$ npm install pm2 -g
```

#### PM2 실행
* watch 옵션 추가하여 실시간 업데이트 적용
```text
$ pm2 start app.js --watch
```

#### 80 Port Redirect 8080
* 80 port로 접속시 8080으로 연결
```
$ sudo iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```