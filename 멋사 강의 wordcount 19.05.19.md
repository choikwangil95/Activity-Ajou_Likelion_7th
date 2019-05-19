# Wordcount

## 1 템플릿언어
### HTML안에 쓰는 장고 제공 언어
HTML안에는 변수나 함수를 사용할 수 없기 때문에 <strong>파이썬 변수/문법등을 쓰고싶을 때 사용</strong>
<br/>
#### 1) 템플릿 변수 
`{{ variable }}` : 해당 파이썬 변수를 HTML파일에 담아 화면에 출력하라 
#### 2) 템플릿 필터
`{{ python_value | filter }}` : filter = length, lower등 필터링을 해준다
#### 3) 템플릿 태그 
`{% tag %}` : HTML상에서 파이썬 문법 사용
```python
class = ["광일","세현","민욱"]
```
```html
# -----------for example------------
number of students = {{ class | length }}

{% for students in class %}

{{students}}

{% endfor %}

# -----------if example--------------
{% if something %}

{% endif %}

# -------------url 생성---------------
{% url 'url_name' %}
```
<br/><br/>

## 2 View 처리
```python
def result(request):
    
    text = request.GET["fulltext"] 
    words = text.split()
    total = len(words)
    word_dictionary = {}
    
    for word in words:
      if word in word_dictionary:
        # increase
        word_dictionary[word] += 1
      else:
        # add dic
        word_dictionary[word] = 1
    
    return render(request, 'result.html', {
        'key' : value,
        'total' : total,
        'words' : words,
        'dictionary' : word_dictionary.items()
 })
```
### 변수 넘겨주기
`text=request.GET["fulltext"]` : 요청받은 값을 데이터로 가져온것을 변수(text)에 저장 (데이터는 name=""으로 지정한 것)<br/>
` return render(request, 'result.html', { 'full' : text } )` :  result.html로 변수를 딕셔너리로 반환해줘야함<br/>

그리고 templates변수는 `{{ full }}` 과 같이 사용해준다 <br/><br/>

### question : 특정 단어가 몇번 사용되었는지 어떻게 확인할 수 있을까?
#### answer : 사전형 자료형을 사용해준다
```python
 word_dictionary = {}
    
    for word in words:
      if word in word_dictionary:
        # increase
        word_dictionary[word] += 1
      else:
        # add dic
        word_dictionary[word] = 1
```
`내 이름은 민철이야 니 이름은 뭐라고? 쟤 이름은 뭐였지?`를 자료형에 저장 `dic = {내 : 1, 이름은 : 1, 민철이야 : 1}`<br/>
여기서 .items() 사용 -> templates에서는 `{% for key, value in dictionary %}` 와 같이 표현해주고 키와 벨류값을 태그로 사용
