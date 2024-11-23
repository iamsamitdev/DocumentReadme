### Workshop Python Django 5 with Next.JS 15 and Supabase
---
### ⚡ Day 1

##### #1 ดาวน์โหลดเอกสารประกอบการเรียนรู้
- [ ] [Django with NextJS and Supabase](https://bit.ly/django-nextjs)

##### #2 Tools & Environment Setup
- [ ] [Python 3.13.x](https://www.python.org/downloads/)
- [ ] [NodeJS 20.x.x](https://nodejs.org/en/download/package-manager/)
- [ ] [Visual Studio Code](https://code.visualstudio.com/download)
- [ ] [Git](https://git-scm.com/downloads)

##### #3 ตรวจสอบเวอร์ชั่นของแต่ละเครื่องมือ
\#3.1 ตรวจสอบเวอร์ชั่นของ Python on Windows

```bash
python --version
pip --version
```
\#3.2 ตรวจสอบเวอร์ชั่นของ Python on Mac OS and Linux
```bash
python3 --version
pip3 --version
```

\#3.2.1 ตรวจสอบเวอร์ชั่นของ NodeJS
```bash
node -v
npm -v
npx -v
```

\#3.3 ตรวจสอบเวอร์ชั่นของ Visual Studio Code
```bash
code --version
```
\#3.4 ตรวจสอบเวอร์ชั่นของ Git
```bash
git --version
```
\#3.5 แนะนำรายชื่อส่วนเสริมของ Visual Studio Code for Python Django
```bash
- Color Picker  by anseki
- Color Highlight by Sergii N
- AutoFileName by JerryHong
- Python by Microsoft
- Django by Baptiste Darthenay
- Material Icon Theme by Philipp Kief
- ES7+ React/Redux/React-Native snippets by dsznajder
- ES7 React/Redux/Styled-components snippets by woodreamz
- Prettier - Code formatter by Prettier
- Thunder Client by Thunder Client
- One Dark Pro by binaryify
```
##### #4. การสร้าง Virtual Enviroment
\#4.1 Windows
```bash
python -m venv env
```

\#4.2 Mac OS and Linux
```bash
python3 -m venv env
```

##### #5. การเปิดใช้งาน Virtual Enviroment
\#5.1 Windows
```bash
env\Scripts\activate
```

\#5.2 Mac OS and Linux
```bash
source env/bin/activate
```

##### #6. การติดตั้ง Django
\#6.1 ติดตั้ง Django 5.1.3
```bash
pip install django==5.1.3
```
\#6.2 เช็ครายการ Package ที่ติดตั้งแล้ว
```bash
pip list
```

##### #7. การสร้าง Project ใน Django
```bash
django-admin startproject firstdjango
```

##### #8. การรันโปรแกรม Django
\#8.1 เข้าไปในโปรเจคที่สร้างขึ้นมา
```bash
cd firstdjango
```

\#8.2 รันโปรแกรม Django
```bash
python manage.py runserver
```
or run with port 8110
```bash
python manage.py runserver 8110
```

##### #9. เรียนรู้ Django Project Structure
```bash
firstdjango
├── firstdjango
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── db.sqlite3
└── manage.py
```

##### #10. การสร้าง View ใน Django
\#10.1 เข้าไปในโปรเจคที่สร้างขึ้นมา
```bash
cd firstdjango
```
\#10.2 สร้างไฟล์ views.py ในโปรเจคบน macOS and Linux
```bash
touch views.py
```
\#10.3 สร้างไฟล์ views.py ในโปรเจคบน Windows
```bash
type nul > views.py
```

\#10.4 แก้ไขไฟล์ views.py
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Welcome to Django AGC")
```

\#10.5 แก้ไขไฟล์ urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('admin/', admin.site.urls),
]
```

##### #11. การกำหนด Path แบบมี Parameter
\#11.1 แก้ไขไฟล์ views.py
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Welcome to Django AGC")

def hello(request, name):
    return HttpResponse(f"Hello {name}")
```

\#11.2 แก้ไขไฟล์ urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('hello/<str:name>', views.hello, name='hello'),
    path('admin/', admin.site.urls),
]
```

##### #12. การสร้าง Template ใน Django
\#12.1 สร้างโฟลเดอร์ templates ในโปรเจคบน macOS and Linux
```bash
mkdir templates
```

\#12.2 แก้ไขไฟล์ settings.py
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'], # แก้ไขบรรทัดนี้
        'APP_DIRS': True,
        ...
    },
]
```

\#12.3 สร้างโฟลเดอร์ templates ในโปรเจคบน Windows
```bash
md templates
```

\#12.4 สร้างไฟล์ index.html ในโฟลเดอร์ templates บน macOS and Linux
```bash
touch templates/index.html
```

\#12.5 สร้างไฟล์ index.html ในโฟลเดอร์ templates บน Windows
```bash
type nul > templates/index.html
```

\#12.6 แก้ไขไฟล์ index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Django AGC</title>
</head>
<body>
    <h1>Welcome to Django AGC</h1>
</body>
</html>
```

\#12.7 แก้ไขไฟล์ views.py
```python
from django.http import HttpResponse
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```

##### #13. การสร้าง Static File ใน Django
\#13.1 สร้างโฟลเดอร์ static ในโปรเจคบน macOS and Linux and Windows
```bash
mkdir static
```

\#13.2 แก้ไขไฟล์ settings.py
```python
import os

STATIC_URL = 'static/'

# แก้ไขบรรทัดนี้สำหรับ development
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]
# แก้ไขบรรทัดนี้สำหรับ production
# STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

\#13.3 สร้างไฟล์ style.css ในโฟลเดอร์ static/css บน macOS and Linux and Windows
```bash
mkdir static/css/style.css
```

\#13.4 แก้ไขไฟล์ style.css
```css
body {
    background-color: #eb5454;
    font-family: Arial, Helvetica, sans-serif;
}
```

\#13.5 แก้ไขไฟล์ index.html
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Django AGC</title>
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
</head>
<body>
    <h1>Welcome to Django AGC</h1>
</body>
</html>
```

\#13.6 การใส่รูปภาพในโปรเจ็กต์ที่ path /static/images/mypic.png
```bash
mkdir static/images
```

\#13.7 คัดลอกไฟล์ mypic.png ไปยังโฟลเดอร์ static/images
```bash
cp mypic.png static/images
```

\#13.8 แก้ไขไฟล์ index.html
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Django AGC</title>
    <link rel="stylesheet" href="{% static '/css/style.css' %}">
</head>
<body>
    <h1>Welcome to Django AGC</h1>
    <img src="{% static '/images/mypic.png' %}" alt="My Picture">
</body>
</html>
```

\#13.9 โครงสร้างโปรเจ็กต์ในตอนนี้
```bash
firstdjango
├── firstdjango
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── static
│   ├── css
│   │   └── style.css
│   └── images
│       └── mypic.png
└── templates
    └── index.html
```

\#13.10 การแทรกค่าของตัวแปรในไฟล์จาก Python ในไฟล์ HTML

\#13.10.1 แก้ไขไฟล์ urls.py
```python
urlpatterns = [
    ...
    # การสร้าง path และรับค่าจาก view
    path('test', views.test, name='test'),
]
```

\#13.10.2 แก้ไขไฟล์ views.py
```python
def test(request):
    # สร้างตัวแปร data และกำหนดค่าให้กับตัวแปร
    data = {'title': 'Django AGC', 'message': 'Welcome to Django AGC'}

    # ส่งค่าตัวแปร data ไปยังไฟล์ test.html
    return render(request, 'test.html', data)
```

\#13.10.3 สร้างไฟล์ test.html ในโฟลเดอร์ templates บน macOS and Linux and Windows
```bash
touch templates/test.html
```

\#13.10.4 แก้ไขไฟล์ test.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>{{ title }}</title>
</head>
<body>
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
</body>
</html>
```

##### #14. Django REST Framework

\#14.1 สร้างแอพพลิเคชันใหม่ชื่อ "todo" ในโปรเจคบน macOS and Linux and Windows
```bash
python manage.py startapp todo
```

\#14.2 แก้ไขไฟล์ settings.py
```python
INSTALLED_APPS = [
    ...
    'todo',
]
```

\#14.3 ติดตั้ง Django REST Framework
```bash
pip install djangorestframework
```

\#14.4 แก้ไขไฟล์ settings.py
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

\#14.5 สร้างไฟล์ model "model.py" ใน firstdjango/models.py
```bash
from django.db import models

class Todo(models.Model): 
    title = models.CharField(max_length=255)
    description = models.TextField()
    completed = models.BooleanField(default=False)
    class Meta:
        app_label = 'todo'
```

\#14.6 สร้างไฟล์ serializer "todoSerializer.py" ใน firstdjango/todoSerializer.py
```bash
from rest_framework import serializers
from .models import Todo

class TodoSerializer(serializers.ModelSerializer):
    class Meta:
        model = Todo
        fields = ['title', 'description', 'completed']
```

\#14.7 สร้างไฟล์ view "todoListView.py" ใน firstdjango/todoListView.py
```bash
from rest_framework.views import APIView
from rest_framework.response import Response
from .models import Todo
from .todoSerializer import TodoSerializer

class TodoListView(APIView):
    def get(self, request):
        todos = Todo.objects.all()
        serializer = TodoSerializer(todos, many=True)
        return Response(serializer.data)
```

\#14.8 แก้ไขไฟล์ urls.py ใน firstdjango/urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views
from .todoListView import TodoListView

urlpatterns = [
    ...
    # API todo
    path('api/todos', TodoListView.as_view(), name='todos'),
]
```

\#14.9 สร้างฐานข้อมูลและสร้างตารางใหม่
```bash
python manage.py makemigrations
python manage.py migrate
```

\#14.10 รันโปรแกรม Django
```bash
python manage.py runserver
```

\#14.11 ทดสอบการทำงานของ API ด้วย Postman/ Thunder Client หรือ Insomnia โดยใช้ URL http://localhost:8000/api/todos
