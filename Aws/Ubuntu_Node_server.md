
de 설치

## AWS Ubuntu 선택 생략

## 1. Ubuntu 안에서 node & npm 설치 및 확인
	sudo apt-get install curl
	curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
	sudo apt-get install -y nodejs

	확인
	node —vsersion
	npm —version

## 2. 소스 작성 - 저장명 server.js
	var http = require('http');
    http.createServer(function(req, res){
        res.writeHead(200, {'Content-Type':'text/plain'});
        res.write('Hello World');
        res.end('<h1>Welcome Ubuntu Sever!</h1>');
    }).listen(3000, function(){
        console.log('Server Running');
    });
    
## 3. AWS Port 설정
	Security Groups 에서 3000 포트 열기
    
## 4. 서버 실행
	node server.js

## 5. 로컬접속 확인 (AWS - ubuntu 안에서 명령어 실행)
	wget http://localhost:3000

## 6. ssh (내 컴퓨터에서 명령어 실행)
	1. pem 이 위치한 폴더로 이동
	2. 명령어 실행 - 두가지로 나뉨
	tunneling 경우
		ssh -i "pem이름.pem" ubuntu@awsPublic주소 -N -L 3030:awsPrivate주소:포트번호
        예시) ssh ssh -i "ubuntuTestServer.pem" ubuntu@52.x.x.x -N -L 3030:172.x.x.x:3000
    그냥 접속하는 경우 (AWS 에서 Connect 했을 때의 example 참고)
    	ssh -i "pem이름.pem" ubuntu@ip주소 or 사이트 주소
        예시) ssh -i "ubuntuTestServer.pem" ubuntu@52.x.x.x
