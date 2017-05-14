# Error Solution : 'No provider for Http!'

## Environment
	angular2+
    Ionic2
    typescript

### in app.module.ts
	Step 1 : add import
    
    	import { HttpModule } from '@angular/http';
        
        
        
    Step 2 : update imports in @NgModule
    
        Before
            imports:[
				BrowserModule,
                IonicModule.forRoot(MyApp)
            ]
            
        After
        	imports:[
				BrowserModule,
                IonicModule.forRoot(MyApp),
                HttpModule
            ]