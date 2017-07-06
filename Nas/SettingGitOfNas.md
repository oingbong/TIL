# SSH 로 NAS의 git 설정 및 외부접속

{:toc}

***

### 필요한 정보
	user ID : root OR admin (처음 접속 할 때)
    Nas IP : 제어판 - 외부 액세스 - DDNS - 외부 주소
    Nas 외부포트번호 (default : 22 or 8022 ?)
    	1. Nas 설치된 공유기 환경에서 url 접속 - 172.30.1.254
    	2. 장치 설정 - 트래픽 관리
    	3. SSH 의 외부포트 확인

***

### 저장할 폴더 만들기
	제어판 - 공유 폴더 - 생성 - gitFile
    
***

### 접속방법
**1. 터미널 실행**
	`ssh -p 외부포트번호 UserID@NAS IP`
	예시
	`ssh -p 8022 root@123.123.123.123`

**2. 비밀번호 입력 (user ID 의 비밀번호)**

**3. gitFile 로 이동**
	`cd /volume1/gitFile/`

**4. git 저장소 폴더 생성 및 이동**
	`mkdir gitrepo.git`
    `cd gitrepo.git`

**5. git 초기 설정**
	`git init --bare`
    `git update-server-info`
    `cd ..`
    `chown -R 사용자명:사용자그룹 gitrepo.git`
    `예시) chown -R gitUser:users gitrepo.git`

**6. 클라이언트에서 접속 (새로운 터미널)**
	`git init`
    `git remote add origin ssh://UserID@NasIP/volume1/gitFile/gitrepo.git`
    OR
    `git remote add origin ssh://UserID@NasIP:port번호/volume1/gitFile/gitrepo.git`
    `git add .`
    `git commit`
    `git push origin master`

***
    
### 에러 및 처리
##### 에러1 - 접속방법 5에서 나타나는 에러
	Operation not permitted
    
    처리방법
	sudo chown -R gitUser:users gitrepo.git
    (sudo 명령어를 붙여줍니다.)


##### 에러2 - 접속방법 6에서 나타나는 에러
	git push origin master 할 경우에 나타나는 에러
    
	Permission denied, please try again.
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.
    
	처리방법
    
	방법 : 제어판 - 사용자 - 사용자 클릭 - 사용자 그룹 - administrators 그룹 추가 - 확인
    이유 : SSH/Telnet은 administrators 그룹에 속하는 계정을 통해서만 시스템에 로그인하는 것을 지원합니다.
    (DSM 도움말 - SSH 검색 - 참고부분)

