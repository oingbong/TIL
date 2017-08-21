### Detect Screen Capture && Alert

#### 내용
1. deinit : 초기화 해제 , deinit 안에 작업내용 작성 자세한 내요은 밑에 URL 참고
2. 밑에 코드는 캡처가 감지될 경우 alert 띄워줍니다. (코드는 블로그 참고)

#### 코드
~~~
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        NotificationCenter.default.addObserver(self, selector: #selector(HtmlViewController.userDidTakeCapture(notification:)), name: .UIApplicationUserDidTakeScreenshot, object: nil)
        }

    deinit {
        NotificationCenter.default.removeObserver(self)
    }


    func userDidTakeCapture(notification: Notification){
        print("캡쳐 감지")
        let titleM = "제목"
        let messageM = "내용"
        let buttonM = "확인"

        let dialog = UIAlertController(title: titleM, message: messageM, preferredStyle: .alert)

        let action = UIAlertAction(title: buttonM, style: UIAlertActionStyle.default)
        dialog.addAction(action)

        self.present(dialog, animated: true, completion: nil)
    }
}
~~~

___


#### 참고
1. 스크린샷 방지
https://swifter.kr/2016/10/22/%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%EC%9D%84-%EC%B0%8D%EC%9D%84-%EB%95%8C-%EA%B0%90%EC%A7%80%ED%95%98%EA%B8%B0/
2. deinit 관련
https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/Deinitialization.html
