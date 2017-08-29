## Node Express 에서 body-parser 사용하기

### body-parser
	Node Express 서버에서 post 형식을 받을 때 body 를 읽어야 하는 부분을 쉽게 처리
    
    
### 사용 방법
	npm install body-parser --save
    
    const bodyParser = require('body-parser');
    
    app.use(bodyParser.urlencoded({extended:true}));
    app.use(bodyParser.json());
