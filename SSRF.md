Austin system has a Server Side Request Forgery vulnerability.  
Austin system url:https://github.com/ZhongFuCheng3y/austin   
The getRemote Url2File in the project reads files based on external remote connections and returns the file content.  
src\main\java\com\java3y\austin\support\utils\AustinFileUtils.java  
![image](https://github.com/biantaibao/Austin_SSRF/assets/131763503/e6a07025-a560-449d-ab69-0108c3267a2b)    
Locate the interface for sending test messages based on the getRemote Url2File method.  
<img width="1258" alt="图片1" src="https://github.com/biantaibao/Austin_SSRF/assets/131763503/67a03b34-82f4-4f44-9afb-0895cb9f3569">    
Among them, the URL is obtained from the message template without any restrictions, and requires a message of email type to make the URL effective.  
src\main\java\com\java3y\austin\handler\handler\impl\EmailHandler.java  
<img width="1274" alt="图片2" src="https://github.com/biantaibao/Austin_SSRF/assets/131763503/02f5e7d0-0c9e-4d8d-8059-9db3de77d8f1">  
Add an email message template to the front-end interface of the system.  
<img width="1427" alt="图片3" src="https://github.com/biantaibao/Austin_SSRF/assets/131763503/57e8d312-ebeb-40ff-b581-0d85d42dfb10">  
![image](https://github.com/biantaibao/Austin_SSRF/assets/131763503/f3afb139-0d2a-4060-8f92-bb8a83bc3ac0)  
Save and Test  
![1704639566_659abc4e637b840d22751](https://github.com/biantaibao/Austin_SSRF/assets/131763503/891dbc38-7af0-4b07-a19a-2a2d820e0b38)  
![image](https://github.com/biantaibao/Austin_SSRF/assets/131763503/7d69d836-a58e-42c5-b8d4-01bdc8321bff)  
The email received a message and carried the passwd attachment.   
![image](https://github.com/biantaibao/Austin_SSRF/assets/131763503/d035af31-32b2-4699-96c6-adb4e9d1d06f)  
![image](https://github.com/biantaibao/Austin_SSRF/assets/131763503/54ba0186-296e-4755-8d9e-81065e22f0de)  

issues url:https://github.com/ZhongFuCheng3y/austin/issues/56









