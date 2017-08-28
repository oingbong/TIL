## 옵셔널 관련

### 상황
	json 요청 후 print 할때 Optional(값) 이 붙는 경우 String 으로 변환, Optional 이 안보이게 해주기
    
### 해결 방법
	let result = json["token"] as! String
    위처럼 as! String 을 붙여주면 print 할 때 Optional 이 생기지 않고 String 변수에 넣는 것이 가능합니다.
    
### Example
	let urlRequest = URLRequest(url: URL(string:"http://www.test.com")!)
        let task = URLSession.shared.dataTask(with: urlRequest){ (data, response, error) in
            if error != nil {
                print(error)
                return
            }
            
            do{
                let json = try JSONSerialization.jsonObject(with: data!, options: .mutableContainers) as! [String: AnyObject]
                
                print("json : \(json)")
                let token = json["token"]
                result = token as! String
                print("result : \(result)")
            } catch let error {
                print(error)
            }
        }
        
        task.resume()
