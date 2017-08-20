# App Transport Security 관련

### App Transport Security
==ATS(줄임)은 HTTP 통신에 관련된 것==
기본값은 NO 로 HTTP 통신을 막아줍니다.
HTTPS은 허용하지만 HTTP도 허용하기 위해서는 info.plist에서 값을 YES로 변경 혹은 추가를 해주어야 합니다.
    
### Settings
1. Info.plist
2. Information Property Settings 옆에 + 버튼 클릭
3. App Transport Security Settings 추가
4. ATS 안에서 Allow Arbitrary Loads 추가
5. 값을 YES 로 변경 혹은 추가

#### 참고
http://blowmj.tistory.com/entry/iOS-iOS9-App-Transport-Security-%EC%84%A4%EC%A0%95%EB%B2%95
