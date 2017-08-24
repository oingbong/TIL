### ViewController Lifecycle

1. 실행순서
    ViewDidLoad : 해당 뷰컨트롤러 클래스 생성될 때 실행
    ViewWillAppear : 뷰 컨트롤러가 화면에 나타나기 직전에 실행
    ViewDidAppear : 뷰 컨트롤러가 화면에 나타난 직후에 실행
    ViewWillDisappear : 뷰 컨트롤러가 화면에 없어지기 전에 실행
    ViewDidDisappear : 뷰 컨트롤러가 화면에 없어진 직후에 실행
    
    2. 설명
    ViewDidLoad : 한번만 실행되므로 초기활 때 사용 (특별한 경우가 아니라면)
    ViewWillAppear : 뷰 컨트롤러 실행 전 해야되는 작업들을 배치하기 좋음
    ViewDidAppear : 애니메이션, API 호출 등을 표시하기 좋음



#### 참고
https://medium.com/ios-development-with-swift/%EC%95%B1-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0-app-lifecycle-vs-%EB%B7%B0-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0-view-lifecycle-in-ios-336ae00d1855
