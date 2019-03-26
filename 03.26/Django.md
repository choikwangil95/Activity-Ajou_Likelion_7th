# Django
## 가상환경이란?
### 어떤 프로젝트를 진행할 때 독립된 공간(프로젝트를 담는 통)/ 이 공간은 전체 영역에 영향을 미치지 않음
### Django package를 설치해야하고 이걸 설치하려면 pip package를 설치해야한다?
### pip package는 파이썬으로 작성된 패키지로 소프트웨어를 설치 및 관리하는 패키지 관리 시스템
### Django = pip 패키지중에 하나인 것임
```
1) 폴더를 열고 새 터미널을 킨다 이때 터미널이 bash가 아니라면 
2) ctrl + shift + p를 눌러서 select default shell을 입력해서 Git bash를 해준다.
3) 가상환경 생성 명령어 : python -m venv 폴더이름
4) 가상환경 실행 명령어 : source myvenv/script/activate
5) 장고 설치 : pip install django

## 장고는 어떻게 작동하는가?
### 장고 프로젝트를 만들어주면 프로젝트 안에 만들어진 파일(App)간의 티키타카로 진행된다.
```
1) django project를 만들어준다 : django-admin startproject (project이름)
만들어주면 다양한 파일들이 생성되는데, 이때 manage.py라는 파일이 서버를 돌린다고 한다.
2) 서버를 작동시키는 명령어 : python manage.py runserver
3) App 은 프로젝트의 작은 구성단위로 app들이 모인것이 프로젝트임
4) App 만들기 : python manage.py startapp (app이름)
5) App 안에는 templates라는 폴더를 하나 만들어줘야한다.
6) 여기서 App과 프로젝트간의 연결을 시켜줘야 한다.
7) App안에서는 templates라는 폴더에서 유저에게 보여질 화면들인 html을 담는다.
8) veiw.py 파일은 유저에게 보여질 화면인 html이 언제 어떻게 처리될지 알려주는 함수이다.
9) url.py는 내가 만든 html이 어떤 url을 입력했을때 뜨게 할지 결정하는것.






```