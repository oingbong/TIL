# .gitignore 설정 후 github 저장소에 적용하기

### Code
	git rm -r --cached .
	git add .
	git commit -m "fixed untracked files"
	git push origin master

### 참고
	http://theeye.pe.kr/archives/2091
