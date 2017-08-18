# Deep Link in Swift

### 1. info.plist 설정
	1) Information Property List 옆에 + 버튼 클릭 후 URL types 선택 아래 두개 추가
    2) URL Schemes - Item : 링크할 이름
    3) URL identifier : Project 의 Bundle Identifier

### 2. AppDelegate.swift 파일 내용 추가 (맨 아래에 추가해 줍니다.)
	extension AppDelegate {
    func application(_ application: UIApplication, open url: URL, sourceApplication: String?, annotation: Any) -> Bool {
        print("url \(url)")
        print("url host : \(url.host!)")
        print("url path : \(url.path)")
        
        let urlPath : String = url.path as String!
        let urlHost : String = url.host as String!
        let mainStoryboard : UIStoryboard = UIStoryboard(name: "Main", bundle: nil)
        
        print("urlPath \(urlPath)")
        print("urlHost \(urlHost)")
        
        // urlHost 에 swift.com 이 포함되어 있지 않으면 기본 페이지 (ViewController 화면을 보여줍니다)
        if urlHost != "swift.com" {
            print("Host is not correct")
            return false
        }
        
        // urlPath 가 있는 경우에만 DetailsViewController 화면을 보여줍니다.
        if !urlPath.isEmpty {
            let detailPage : DetailsViewController = mainStoryboard.instantiateViewController(withIdentifier: "DetailsViewController") as! DetailsViewController
            self.window?.rootViewController = detailPage
        }
        
        self.window?.makeKeyAndVisible()
        return true
        
    }
}

### 3. 실행방법
	url 에 info.plist 에 설정한 URL Schemes 와 host , path 를 설정해줍니다.
    ex) info.plist 에 설정한 이름이 swiftDeep 이라면
    swfitDeep://swift.com/helloworld
    URL Schemes + :// + host + path


#### 참고
https://www.youtube.com/watch?v=ZADKJwsllqg
