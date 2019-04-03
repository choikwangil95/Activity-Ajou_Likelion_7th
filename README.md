# 19.04.03 멋쟁이 사자처럼 강의
## 1_부트스트랩으로 css꾸미기
#### CDN이란? content delivery network


## 2_base html 파일을 만들어서 css를 다양한 html파일들에 한번에 적용하기

#### 1) 프로젝트폴더의 하위 프로젝트폴더에 templates폴더를 만들어주고 base.html파일을 만들어준다.
#### 2) base.html파일에는 적용할 내용만 남겨둔다
```html
<body>
    <div class="container">
        {%block content%}                             # 여기서 이 block content와 endblock사이에 
        {% endblock%}                                 # 다른 html 파일이 들어가는 것
    </div>
</body>
```
#### 3) base.html block내부에 들어갈 html 파일은 다음과 같이 해준다.
```html
{% extends 'base.html' %}                             # 다음과 같이 extends를 해주고

{% block content%}                                    # base파일의 block 부분에 들어갈 내용을 써준다. 

<h1>환전계산값 : {{totalvalue}}</h1>                   # content의 이름은 마음대로 할 수 있따.

<p> 한국 돈 : {{fulltext}} 원</p>

{% endblock%}
```
## 3_Font 적용해주기
#### 1) 프로젝트파일에 static 폴더를 만들어주고 css폴더를 만들어주고 css파일을 만들어준다.
#### 2) noonnu사이트에 들어가서 웹폰트로 사용하기를 복사하여 css파일에 넣어준다
```css
@font-face {                                          # 눈누로 부터 폰트를 가져온 것
    font-family: 'S-CoreDream-8Heavy';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_six@1.2/S-CoreDream-8Heavy.woff') format('woff'); 
    font-weight: normal; 
    font-style: normal; 
}

*{
    font-family: 'S-CoreDream-8Heavy';                 # * selector는 모든 elements를 정의하는 것
}
```
#### 3) base.html파일에 이 css파일을 <link> 해준다.
```html
{% load static%}

<link rel="stylesheet" type="text/css" media="screen" href="{% static 'css/style.css' %}">
```

## 4_이미지 가져다 쓰기
#### 1) font awesome에서 svg를 클릭해준 다음 scripts를 base.html body tag에 추가해준다
```html
<script defer src="https://use.fontawesome.com/releases/v5.8.1/js/all.js" integrity="sha384-g5uSoOSBd7KkhAMlnQILrecXvzst9TdC09/VM+pjDTCM+1il8RHz5fKANTFFb+gQ" crossorigin="anonymous"></script>
```
#### 2) 원하는 이미지를 찾고 html 파일에 써준다.
