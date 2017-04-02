# Phantomjs 및 Casperjs 설치하기

### 주의사항
    1. Casperjs 는 Phantomjs 기반이므로 Casperjs 사용하기 위해서는 Phantomjs 를 먼저 설치해야 합니다.
    2. Casperjs 는 npm을 통해 설치할 수 있지만 NodeJS 모듈은 아닙니다.
        노드에서 require('casperjs')를 사용하여 로드 할 수 없습니다.
        (라고 공식사이트에 나와있습니다.)

### 목차
	1. phantomjs 설치하기
	2. phantomjs PATH 설정
	3. casperjs 설치하기
	4. casperjs 설정 변경

### phantomjs 설치하기
	1. npm install -g phantomjs
	2. phantomjs -v
	
버전 확인시에 command not found 라고 나오면 PATH 설정을 해야 합니다.
    
### phantomjs PATH 설정
	1. cd ~
	(상단 디렉토리로 이동)
    2. open -e .bash_profile
    (없는 경우 touch .bash_profile) 로 만듭니다.
    3. 안에 내용을 채워줍니다.
    두 개의 형식 중 사용자가 원하는 형식으로 입력합니다.(개인적으로는 2번)
    
    	1번 형식
        export PATH=${PATH}:/Users/{사용자컴퓨터명}/Documents/study/webScrap/phantomjs-2.1.1-macosx/bin:
        2번 형식
        export phantomjs=/Users/{사용자컴퓨터명}/Documents/study/webScrap/phantomjs-2.1.1-macosx 
		export PATH=${PATH}:${phantomjs}/bin:
        
    4. 터미널 다시 실행
    5. phantomjs -v
	(버전 확인)
    
### casperjs 설치하기
	1. npm install -g casperjs
	2. casperjs --version
	
### casperjs 설정 변경
    경로 이동
    1. finder 에서 Command + Shift + G
    2. /usr/local/lib/node_modules/casperjs/bin 이동
    3. bootstrap.js 열기
    4. 두 가지 작업 진행합니다.
        1. function __die 와 function __terminate 주석 막기
        2. function has 위에 문장 추가
            var system = require('system'); 
            var argsdeprecated=system.args; 
            argsdeprecated.shift(); 
            phantom.args=argsdeprecated;
    5. 터미널 다시 실행
    6. casperjs --version
