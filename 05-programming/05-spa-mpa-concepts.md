---
title: "6주차 SPA,MPA 개념 이해하기"
date: 2026-08-23
updated: 2026-11-11
category: "프로그래밍 기초"
tags: ["알토르IT기초과정"]
original: https://velog.io/@xjoker7272/6%EC%A3%BC%EC%B0%A8-SPAMPA-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0
---

### - 파이썬 기본 문법 찾아보면서 경험해보기
   - vscode에서 파이썬 익스텐션을 설치 하기 - 파이썬 설치 - claude code한테 요청하면 알아서 해줌
### - 파이썬 Flask 가 무엇인지 ? API는 무엇인지 정리해보기

## 1. Flask란?
- Flask는 파이썬 기반 웹 프레임워크중 하나입니다. 자바가 아닌 파이썬으로도 웹 서버를 만들 수 있다는 의미입니다.

- 자바 기반 웹 프레임워크로는 대표적으로 Spring이 있듯이, 파이썬 기반 웹 프레임 워크로는 대표적으로 Flask, Django가 있는 것입니다.

## 2. 여기서 프레임워크란?

- 프로그래밍에서 특정 운영 체제를 위한 응용 프로그램 표준 구조를 구현하는 라이브러리 모음입니다.

## 3.그럼 Flask는 언제 쓰이는가?
- 앞에서 언급했듯이, 파이썬 기반으로 웹 개발을 하고싶을 때 사용할 수 있습니다. 파이썬이 back-end쪽을 담당하고 HTML, CSS, JAVASCRIPT이 Front-end쪽을 담당하게 하는식으로 구현하여 웹 프로젝트를 수행할 수 있습니다.

- 이미지, 영상처리, AI 관련 프로그램을 개발하는데에는 파이썬이 많은 사랑을 받고 있는데, 파이썬으로 성능 좋고 빠른 훌륭한 라이브러리들을 많이 접할 수 있기 때문입니다. Spring같은 다른 언어 기반의 웹 프레임워크로 주로 서비스를 하다가 특정 이미지나 영상은 파이썬 코드로 따로 처리하고자 하는 경우에 유용하게 쓰일 것입니다. Spring 서버에서 Flask 서버로 파일을 전송하면 Flask 서버에서 해당 파일을 받아 파이썬 코드로 원하는대로 처리해주고, 다시 Spring 서버로 돌아오는 식으로 진행이 가능한 것입니다.

## 4. API 는 무엇인가?
- API (Application Programming Interface)는 서로 다른 프로그램이나 시스템이 데이터를 안전하고 규칙적으로 주고받을 수 있도록 이어주는 '소통의 다리' 또는 '주문 창구'를 뜻합니다.

- IT 업계에서 API를 설명할 때 가장 많이 쓰는 찰떡같은 비유가 바로 '레스토랑의 웨이터'입니다.

- 손님 (클라이언트/브라우저): 식당에 와서 메뉴판을 보고 음식을 고릅니다. 주방에서 불 조절을 어떻게 하는지, 칼질을 어떻게 하는지는 알 필요가 없습니다.

- 요리사 (서버 및 데이터베이스): 복잡한 시스템 안에서 재료를 다듬고 실제 요리(데이터 처리)를 합니다.

- 웨이터 (API): 손님의 주문(요청)을 규격에 맞게 주방에 전달하고, 주방에서 완성된 요리(결과 데이터)를 다시 손님에게 가져다주는 매개체 역할을 합니다.

### - localhost:3000/hello 하고 입력하면 브라우저 화면에 hello가 찍혀나오게 

- http://localhost:3000/hello

### -그럼 html에서의 hello 출력의 차이는 무엇인가?

#### 1. HTML 파일로 띄우는 방식 (정적 - Static)(MPA)
- 비유: 이미 인쇄가 끝난 '전단지'나 '메뉴판'과 같습니다.

- 작동 원리: index.html 파일을 더블클릭해서 열면, 브라우저가 하드디스크에 저장된 텍스트를 있는 그대로 읽어서 화면에 보여주기만 합니다.

- 특징: 파일 안에 적힌 내용이 영구적으로 고정되어 있습니다. 방문자가 누구든, 낮이든 밤이든 무조건 똑같은 화면만 보여줍니다. 연산이나 판단을 할 수 있는 '뇌(Logic)'가 없습니다.

####  2. 파이썬(Flask) 서버로 띄우는 방식 (동적 - Dynamic)(SPA)
- 비유: 식당에서 주문을 받고 요리를 내어주는 '요리사' 또는 '안내 데스크 직원'과 같습니다.

- 작동 원리: 브라우저가 localhost:3000/hello로 "hello 페이지 줘!"라고 요청(Request)을 보내면, 파이썬 프로그램이 그 요청을 듣고 코드를 실행하여 "hello"라는 글자를 실시간으로 생성해서 응답(Response)해 줍니다.

- 특징: 프로그램이 스스로 생각하고 행동할 수 있습니다. 예를 들어 코드를 조금만 수정하면, 아침에 접속하면 "Good Morning", 저녁에 접속하면 "Good Evening"을 출력하게 하거나, 데이터베이스에서 로그인한 사용자의 이름을 찾아서 "Hello, Leo님!"이라고 맞춤형 글자를 찍어낼 수도 있습니다.

### - http의 get과 post메소드가 무엇인지 찾아보기

#### GET의 특징

- GET 요청은 캐시가 가능합니다. 
 : GET을 통해 서버에 리소스를 요청할 때 웹 캐시가 요청을 가로채 서버로부터 리소스를 다시 다운로드하는 대신 리소스의 복사본을 반환합니다. HTTP 헤더에서 cache-control 헤더를 통해 캐시 옵션을 지정할 수 있습니다.
 
>여기서 캐시(cache)란?
- 캐시(Cache)는 IT와 컴퓨터 과학 분야에서 '데이터를 임시로 복사해 두는 아주 빠른 저장소'를 의미합니다. (어원은 프랑스어로 '무언가를 숨겨두는 장소'라는 뜻에서 유래했습니다.)-
- 이해하기 쉽게 '책상 서랍'에 비유할 수 있습니다.
- 원본 서버 또는 하드디스크 (도서관): 자료가 아주 많지만, 매번 직접 가서 찾아오려면 시간이 오래 걸립니다.
- 캐시 (책상 서랍): 보관할 수 있는 공간은 좁지만, 지금 당장 자주 쓰는 자료를 넣어두고 1초 만에 바로바로 꺼내 볼 수 있습니다.

- GET 요청은 브라우저 히스토리에 남습니다.

- GET 요청은 북마크 될 수 있습니다.

- GET 요청은 길이 제한이 있습니다.


- ``` GET 요청의 길이 제한은 표준이 따로 있는건 아니고 브라우저마다 제한이 다르다고 합니다.```


- GET 요청은 중요한 정보를 다루면 안된다. ( 보안 )


- ```GET 요청은 파라미터에 다 노출되어 버리기 때문에 최소한의 보안 의식이라 생각하면 됩니다.```

>여기서 파라미터(Parameter)란?
- 파라미터(Parameter)는 프로그래밍과 IT 분야에서 '함수나 시스템이 외부로부터 데이터를 전달받기 위해 뚫어놓은 통로(또는 변수)'를 뜻합니다. 우리말로는 주로 '매개변수'라고 번역합니다.
- 이해하기 쉽게 '자판기'나 '믹서기'에 비유할 수 있습니다.
🥤 자판기 비유로 이해하기
- 함수 (시스템): 음료수를 뽑아주는 자판기
파라미터 (Parameter): 자판기에 뚫려 있는 '동전 투입구' (무언가 들어올 것이라고 정해놓은 자리)
- 인자 (Argument): 투입구에 실제로 집어넣는 '500원짜리 동전' (실제로 전달되는 진짜 데이터)

- GET은 데이터를 요청할때만 사용 됩니다.

#### POST의 특징

- POST 요청은 캐시되지 않는다.

- POST 요청은 브라우저 히스토리에 남지 않는다.

- POST 요청은 북마크 되지 않는다.

- POST 요청은 데이터 길이에 제한이 없다.

### - http 이용을 해서 서버에게 데이터를 보내는 다양한 방식(content-type)이 무엇이 있는지 정리 해보기
   - queryString
    - Query String(쿼리 스트링)은 앞서 설명해 드린 GET 메서드가 서버로 데이터를 전달할 때 사용하는 핵심 방식입니다.

쉽게 말해, 웹 주소(URL) 맨 끝에 꼬리표처럼 매달아서 서버로 보내는 데이터 문자열을 의미합니다.

### Query String의 구조
URL 뒤에 물음표(?)를 붙여서 "여기서부터 데이터 전달이 시작됩니다"라고 알린 뒤, 변수이름=값 형태로 데이터를 나열합니다. 전달할 데이터가 여러 개일 때는 앰퍼샌드(&) 기호를 사용해 쇠사슬처럼 연결해 줍니다.

기본 뼈대: http://웹사이트주소/경로?이름1=값1&이름2=값2

실제 예시: 구글에서 'python'을 검색했을 때의 주소 형태
>https://www.google.com/search?q=python&hl=ko]
(https://www.google.com/search?q=python&hl=ko)

? : 지금부터 데이터를 보냅니다.

q=python : 검색어(q)는 'python'입니다.

& : 그리고

hl=ko : 언어(hl)는 '한국어(ko)'로 설정해 주세요.

- 검색 및 필터링: 쇼핑몰에서 특정 조건을 걸어 검색할 때
(?category=shoes&color=black&size=270)

- 페이지 이동 (Pagination): 게시판에서 다음 페이지로 넘어갈 때 (?page=3)

- 유입 경로 추적 (Tracking): 마케팅 광고 링크를 통해 사용자가 어디서 접속했는지 통계를 낼 때 (?source=youtube&campaign=summer_sale)
### form-data의 구조

- URL이 아닌 HTTP 통신의 본문(Body) 안에 데이터를 숨겨서 보냅니다. 이때 서로 다른 종류의 데이터(텍스트, 파일)가 한 상자 안에서 섞이지 않도록 무작위 문자열인 '칸막이(Boundary)'를 쳐서 구역을 확실하게 나눕니다.

- 기본 뼈대: (HTTP 메시지 본문 내부)
--칸막이
- 이름1: 텍스트 값
--칸막이
- 이름2: 첨부파일 데이터
--칸막이--

- 실제 예시: 회원가입 시 닉네임('leo')과 프로필 사진('profile.jpg')을 동시에 전송할 때의 내부 데이터 형태
------WebKitFormBoundary7MA4
Content-Disposition: form-data; name="nickname"

#### form-data 예시
leo
------WebKitFormBoundary7MA4
Content-Disposition: form-data; name="profile_image"; filename="profile.jpg"
Content-Type: image/jpeg

- (실제 이미지의 알 수 없는 바이너리 데이터)
------WebKitFormBoundary7MA4--

- ------WebKitFormBoundary... : "지금부터 첫 번째 데이터를 담는 구역(칸막이)입니다."

- name="nickname" : 데이터의 이름표는 'nickname'입니다.

- leo : 실제 전달되는 닉네임 텍스트 값입니다.

- ------WebKitFormBoundary... : "다음 데이터를 담기 위해 다시 칸막이를 칩니다."

- filename="profile.jpg" : "이 데이터는 'profile.jpg'라는 이름의 파일입니다."

- Content-Type: image/jpeg : "이 파일의 진짜 정체(종류)는 이미지입니다."

- ------WebKitFormBoundary...-- : "모든 데이터 전송이 끝났습니다." (끝에 --가 붙음)
### form-urlencoded의 구조

- URL이 아닌 HTTP 통신의 본문(Body) 안에 데이터를 담아 보내지만, 데이터를 나열하는 규칙은 쿼리 스트링과 완전히 똑같습니다. 이름 그대로 데이터를 URL 문자열 형식으로 '인코딩(변환)'해서 전송합니다.

- 기본 뼈대: (HTTP 메시지 본문 내부)
이름1=값1&이름2=값2

- 실제 예시: 로그인 화면에서 아이디('admin')와 비밀번호('1234')를 입력하고 [로그인] 버튼을 눌렀을 때의 내부 데이터 형태
(HTTP 헤더 부분)
Content-Type: application/x-www-form-urlencoded

(HTTP 메시지 본문 부분)
id=admin&password=1234

- Content-Type: ...urlencoded : "지금 보내는 데이터는 일반적인 텍스트 폼(form) 형태입니다"라고 서버에 미리 알려줍니다.

- id=admin : 아이디(id)는 'admin'입니다.

- & : 그리고

- password=1234 : 비밀번호(password)는 '1234'입니다.

- 특징 (인코딩): 만약 아이디가 한글로 '관리자'라면, 웹 표준 규칙에 따라 글자가 깨지지 않도록 %EA%B4%80%EB%A6%AC%EC%9E%90 같은 복잡한 기호로 자동 변환(URL 인코딩)되어 전송됩니다.

#### 실무에서는 언제 주로 사용할까요?

- 파일 전송 없이 오직 '글자(텍스트)'로만 이루어진 정보를 POST 방식으로 주소창에 노출하지 않고 안전하게 서버로 제출할 때 가장 기본적으로 쓰입니다.

- 보안이 필요한 텍스트 전송 (로그인): 비밀번호나 주민등록번호처럼 검색용 쿼리 스트링(주소창 노출)으로 보내면 절대 안 되는 민감한 텍스트 정보를 제출할 때

- 간단한 웹 양식 제출: 첨부파일 기능이 없는 단순한 회원가입 폼, 짧은 설문조사, 텍스트로만 이루어진 Q&A 게시글을 등록할 때

- 오래된 시스템(Legacy)과의 통신: 최신 방식인 JSON을 인식하지 못하는 과거의 구형 웹 서버나 특정 결제 모듈(PG)과 텍스트 데이터를 주고받아야 할 때
### JSON의 구조

- URL이 아닌 HTTP 통신의 본문(Body) 안에 데이터를 담아 보냅니다. 앞서 살펴본 방식들처럼 & 기호로 무작정 한 줄로 이어 붙이는 대신, 키(Key)와 값(Value)이 명확하게 짝을 이루며 계층(트리) 구조를 가질 수 있습니다.

- 기본 뼈대: (HTTP 메시지 본문 내부)
{ "이름1": "값1", "이름2": "값2" }

- 실제 예시: 회원 정보와 그 회원이 가진 권한(목록)을 동시에 서버로 전송할 때의 내부 데이터 형태
(HTTP 헤더 부분)
Content-Type: application/json

- (HTTP 메시지 본문 부분)
{
  "id": "admin",
  "password": "1234",
  "roles": ["user", "manager"]
}

- Content-Type: application/json : "지금 보내는 데이터는 JSON 규격으로 작성되었습니다"라고 서버에 명확히 알려줍니다.

- { } (중괄호) : "여기서부터 여기까지가 하나의 데이터 묶음(객체)입니다"라는 뜻입니다.

- "id": "admin" : 아이디(id)는 'admin'입니다. (문자열 데이터는 반드시 큰따옴표로 감쌉니다)

- "roles": [...] : 앞서 배운 폼(form) 방식들과 다르게 대괄호 [ ]를 사용하여 "이 사용자는 일반 유저와 매니저 권한 2개를 동시에 가집니다"처럼 '목록(배열)' 형태의 데이터를 아주 직관적으로 표현할 수 있습니다.

#### 실무에서는 언제 주로 사용할까요?

- 파일 업로드(사진, 영상 등)를 제외한 거의 모든 현대 웹/앱 서비스의 '데이터 통신'에 사실상 기본값(Default)으로 사용됩니다.

- RESTful API 통신: 브라우저 화면 전체를 새로고침하지 않고, 화면 뒤에서 조용히 서버와 데이터를 주고받을 때 (예: 유튜브에서 '좋아요' 버튼을 눌렀을 때, 넷플릭스 영화 목록을 더 불러올 때)

- 복잡한 구조의 데이터 전송: "회사 정보 아래에 3개의 부서가 있고, 각 부서마다 5명의 직원이 있는" 식의 복잡하게 중첩된 데이터를 전송할 때

- 이 기종 간의 통신: 파이썬(백엔드), 자바스크립트(웹), 스위프트(아이폰), 코틀린(안드로이드) 등 서로 다른 프로그래밍 언어를 쓰는 환경에서도 누구나 공통으로 이해할 수 있는 완벽한 중간 통역사 역할을 합니다.

### - 이 보내는 방식에 따라서 파이썬 flask에서 받아오는 방식이 달라진다.

### 🛠️ 준비 작업
어떤 방식이든, 먼저 코드 맨 위에 request 도구를 가져와야 합니다.


```python
from flask import Flask, request
```

#### 1. 🧩 쿼리 스트링 (Query String) 받을 때
보낸 방식: GET http://localhost:3000/search?keyword=apple

Flask의 도구: request.args (주소창의 '인자(arguments)'를 읽어옵니다)

받는 코드:


```python
@app.route('/search', methods=['GET'])
def search():
# 주소창 꼬리표에서 'keyword'라는 이름의 값을 꺼냅니다.
user_keyword = request.args.get('keyword') 
return f"검색하신 단어는 {user_keyword} 입니다."
```

#### 2. 📝 폼 데이터 (form-urlencoded) 받을 때
보낸 방식: 텍스트만 폼에 담아서 POST로 전송 (id=admin&password=1234)

Flask의 도구: request.form (제출된 폼 서류를 읽어옵니다)

받는 코드:

```python
@app.route('/login', methods=['POST'])
def login():
# 보이지 않는 본문(Body) 서류에서 'id'와 'password'를 꺼냅니다.
user_id = request.form.get('id')
user_pw = request.form.get('password')
return f"환영합니다, {user_id}님!"
```

#### 3. 📦 폼 데이터 (multipart/form-data) 받을 때
보낸 방식: 텍스트와 사진 파일을 한 상자에 담아서 POST로 전송

Flask의 도구: 텍스트는 request.form, 파일은 request.files로 분리해서 꺼냅니다.

받는 코드:
```python
@app.route('/upload', methods=['POST'])
def upload_profile():
# 1. 텍스트 정보 꺼내기
nickname = request.form.get('nickname')

# 2. 파일 정보 꺼내기 (주의: files 사용)
profile_img = request.files.get('profile_image')

# 파일을 서버 컴퓨터에 저장하는 명령어
profile_img.save(f"./uploads/{profile_img.filename}")
return f"{nickname}님의 사진 업로드 완료!"
```

#### 4. 🚀 제이슨 (application/json) 받을 때
보낸 방식: 중괄호 { "title": "hello", "content": "world" } 형태로 POST 전송

Flask의 도구: request.json 또는 request.get_json() (JSON 데이터를 파이썬 사전 객체로 자동 변환해 줍니다)

받는 코드:
```python
@app.route('/api/post', methods=['POST'])
def create_post():
    # JSON 포장지를 뜯어서 파이썬 딕셔너리로 만듭니다.
    data = request.get_json()

    title = data.get('title')
    content = data.get('content')
    return f"제목: {title}, 내용: {content} 저장 완료!"
```

