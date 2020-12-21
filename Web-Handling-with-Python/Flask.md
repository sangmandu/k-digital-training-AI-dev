# Flask
+ Python 기반 **마이크로 웹 프레임워크**
+ 각각의 프로젝트에 맞는 독립적인 환경을 구성하는 것이 프로젝트 관리가 편리해짐
   + **가상환경** 개념 
+ 목적에 따른 모듈만 있는 환경을 구축해서 관리하면 편하지 않을까?

   + **마이크로 웹 프레임 워크**?
      + 핵심 기능만 간결하게 유지하지만, 확장 가능한 것을 목적으로하는 프레임워크
      + 즉, 특별한 도구나 라이브러리가 필요없기 때문에 마이크로 프레임 워크라고 부름
      
### 가상환경 및 Flask 설치하기      

+ 가상환경 설치   
 ```python
 pip install virtualenv
 ```

+ 가상환경 생성  
 ```python
 virtualenv venv
 ```
  > 일반적으로 가상환경 이름을 venv으로 설정함

+ 가상환경 진입  
   + 윈도우   
    ```python
    cd venv/Scripts/activate.bat
    ```
   
   + 우분투
    ```python
    source venv/bin/activate
    ```

+ 가상환경 진입 후 flask 설치
 ```python
 pip install flask
 ```

-----------------------------------------

# 인터넷과 웹   

### 인터넷(Internet)
+ 전 세계 컴퓨터를 하나로 합치는 거대한 **통신망**

### 웹(Web)
+ 인터넷에 연결된 사용자들이 정보를 공유할 수 있는 **공간**
+ **클라이언트**(Client)와 **서버**(Server) 사이의 소통
   + **클라이언트**가 서버에 **정보를 요청** 🖥 → 🖥 (Request)
   + **서버**는 요청받은 정보에 대한 **처리 진행** 
   + **서버**가 클라이언트의 요청에 대해 **응답** 🖥 ← 🖥 (Response)


----------------------------------------------
# Flask with REST API

### API
+ 프로그램들이 서로 상호작용하는것을 도와주는 **매개체**

### REST(Representational State Transfer)
+ 웹 서버가 요청을 응답하는 방법론 중 하나
+ 데이터가 아닌 **자원(resource)** 의 관점으로 접근

### REST API 
+ **HTTP URI**를 통해 리소스를 명시하고 **HTTP Method**를 통해 해당 리소스에 대한 CRUD(Create, Read, Update, Delet)를 진행
   + 웹 상에서의 리소스를 고유하게 식별할 수 있도록 하는 것(웹 상에서 정보를 요청할때 대상하는 위치에 대한 식별자)
   + URI에 속하는 URL, URN이 있음 
      + [[HTTP] URI, URL 구조](https://victorydntmd.tistory.com/287)
   + URL : 특정 서버의 한 리소스에 대해 구체적인 위치
   + URN : 리소스가 어디에 위치해 있든 찾을 수 있는 방식   
   
      <img src="https://user-images.githubusercontent.com/72974863/102746040-c8587200-43a0-11eb-8a58-1ad62ba266e1.png" width="30%" height="30%">
      
+ 구성
   + 자원(Resurce) : URI
   + 행위(Verb) : HTTP Method
   + 표현(Representations)
   
+ REST API 설계시 가장 중요한 항목 
   + **URI**는 정보의 리소스를 표현
      + 리소스명은 명사를 사용(동사적 의미 X)
   + 리소스에 대한 행위는 **HTTP Method(POST, GET, PUT, DELETE)**로 표현
      + **POST** : POST를 통해 해당 URI 요청하면 리소스 생성
      + **GET** : GET을 통해 해당 리스트 조회 및 자세한 정보 가져오기
      + **PUT** : PUT을 통해 해당 리소스 수정
      + **DELETE** : DELETE를 통해 리소스 삭제
   
+ REST의 특징
   + **무상태성(stateless)** : 클라이언트의 상태정보를 따로 저장하고 관리하지 X
   + **캐시 가능(Cacheable)** : HTTP 웹표준을 그대로 사용해서, 웹에 사용하는 기존 인프라를 그대로 활용 가능
   + **클라이언트-서버 구조** 등 ...   
   
   
✔ [REST API 정리잘한 다른사람의 블로그 참고하기👀](https://meetup.toast.com/posts/92)

### Postman
+ **개발한 API를 테스트**하고, 테스트한 결과를 공유해서 **API 개발의 생산성을 높여주는 API 툴**
+ [Postman 다운로드](https://www.getpostman.com/downloads/)
+ 많이 사용하는 Collections, Code generate, Manage environments, Interceptor 4가지 
    
    
✔ [Postman 개요 정리잘한 다른사람의 블로그 참고하기👀](https://meetup.toast.com/posts/107)

