# Using global color(?) in ionic Project

### Before 
	<ion-navbar>
	</ion-navbar> 

### After
	<ion-navbar color=“primary">
	</ion-navbar>

### Explain
	src/theme/variables.scss 에서$color:() 안에 정의된 것을 사용
	형태 -> 키워드 : #색상코드 로 되어있으며 밑에 정의된 예시 참고
	정의를 하고 각 페이지에서 사용
    
### In variables.scss (Example)
    $colors: (
        primary:    #488aff,
        secondary:  #32db64,
        danger:     #f53d3d,
        light:      #f4f4f4,
        dark:       #222
    );