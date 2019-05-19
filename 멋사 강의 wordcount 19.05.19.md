# Wordcount

## 1 템플릿언어
### HTML안에 쓰는 장고 제공 언어
HTML안에는 변수나 함수를 사용할 수 없기 때문에 <strong>파이썬 변수/문법등을 쓰고싶을 때 사용</strong>
<br/>
- 1) 템플릿 변수 
`{{ variable }}` : 해당 파이썬 변수를 HTML파일에 담아 화면에 출력하라 
- 2) 템플릿 필터
`{{ python_value | filter }}` : filter = length, lower등 필터링을 해준다
- 3) 템플릿 태그 
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

