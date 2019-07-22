# login custom
장고에는 기본적으로 auth라는 object가 있고 그 안에<br/>
authnizition, login, logout, user 등 다양한 기능들이 있지만 어떻게 돌아가는지 몰라서 내가 해봄
```python
# models.py

class Userdata(models.Model):
    userID = models.CharField(max_length=100)
    userPW_1 = models.CharField(max_length=100)
    userPW_2 = models.CharField(max_length=100)
    userEmail = models.CharField(max_length=100)
    userNickname = models.CharField(max_length=100)
    objects = models.Manager()
    last_login = models.DateTimeField(auto_now_add=True, null = True)

    def __str__(self):
        return self.userNickname
```

```python
# forms.py

class UsersignupForm(forms.ModelForm): 
    class Meta:
        model = Userdata
        fields = ('userID', 'userPW_1', 'userPW_2', 'userEmail', 'userNickname')
        labels = {  # input의 label 정의
            'userID' : '아아디' ,
            'userPW_1' : '비밀번호',
            'userPW_2' : '비밀번호 확인',
            'userEmail' : '이메일',
            'userNickname' : '닉네임',
        }
        widgets = { # form의 특징과 속성 정의
            'userID' : forms.TextInput,
            'userPW_1' : forms.TextInput,
            'userPW_2' : forms.TextInput,
            'userEmail' : forms.TextInput,
            'userNickname' : forms.TextInput,
        }

class UserloginForm(forms.ModelForm): 
    class Meta:
        model = Userdata
        fields = ('userID', 'userPW_1')
        labels = {  # input의 label 정의
            'userID' : '아아디' ,
            'userPW_1' : '비밀번호',
        }
        widgets = { # form의 특징과 속성 정의
            'userID' : forms.TextInput,
            'userPW_1' : forms.TextInput,
        }
```

```python
# views.py
def logout(request):
    if request.method == 'POST':
        auth.logout(request)
        return redirect('signin')
    return render(request, 'signup.html')

def signup(request):
    if request.method == "POST":
        form = UsersignupForm(request.POST)
        if request.POST['userPW_1'] == request.POST['userPW_2']:
            try:
                user = Userdata.objects.get(userID=request.POST['userID'])
                if user:
                    return render(request, 'signup.html', {'error': 'Username has already been taken'})
            except:
                if form.is_valid():
                    form.save()
                    return redirect('qa_list') 
    else:
        form = UsersignupForm()
        return render (request, 'signup.html', {'form' : form})

def signin(request):
    if request.method == "POST":
        user_id = request.POST['userID']
        user_pw = request.POST['userPW_1']
        valid_id = Userdata.objects.filter(userID = user_id)
        valid_pw = Userdata.objects.filter(userPW_1 = user_pw)

        if valid_id and valid_pw:
            try:
                user = Userdata.objects.get(userID=user_id)
            except:
                user = Userdata(userID=user_id)
                user.save()

            if user is not None:
                auth.login(request, user)
                return redirect('qa_list')
        else:
            form = UserloginForm()
            return render(request, 'signin.html', {
                'error': 'username or password is incorrect.',
                'form' : form
            })
    else:
        form = UserloginForm()
        return render(request, 'signin.html', {'form': form})
```
```html
# html
{% if user %}
        <p>{{Userdata.}}</p>
        <div class = "button1">
                <a class="dropdown-item" href="javascript:{document.getElementById('logout').submit()}">Logout</a>
            <form id="logout" method="POST" action="{% url 'logout' %}">
                {% csrf_token %}
                <input type="hidden" />
            </form>
        </div>
        <div class = "button1">
            <a href="{% url 'qa_new' %}">질문하러 가기</a>
        </div>
        </br>
        {% else %}
        <div class = "button1">
            <a href="{% url 'signup' %}">회원가입</a>
        </div>
        <div class = "button1">
            <a href="{% url 'signin' %}">로그인</a>
        </div>
        {% endif %}

        <p>user에게 작성된 질문 개수 : {{number}}</p>
        
        {% for qa in userqas %}
            <div class="user_question">
            <a href="{% url 'qa_detail' qa.id %}"><p>Q {{qa.title}} </p></a>
            </div>
        {% endfor %}
```
