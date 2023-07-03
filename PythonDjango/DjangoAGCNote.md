### Basic to Advance Python Django with AGC
---
### ⚡ Day 1

##### #1 ดาวน์โหลดเอกสารประกอบการเรียนรู้
- [ ] [Python Django with AGC](bit.ly/django-agc)

##### #2 Tools & Environment Setup
- [ ] [Python 3.11.x](https://www.python.org/downloads/)
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
- Python by Microsoft
- Django by Baptiste Darthenay
- AutoFileName by JerryHong
- Material Icon Theme by Philipp Kief
- Highlight Matching Tag by vincaslt
- Djaneiro - Django Snippets by Scott Barkman
- Copy Django model fields by baterson
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
\#6.1 ติดตั้ง Django 4.2.2
```bash
pip install django==4.2.2
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

### ⚡ Day 2

#### Build a Blog Application

##### หัวข้อการเรียนรู้
1. การสร้างโปรเจ็กต์ใหม่ใน Django
2. การ Migrate ฐานข้อมูลพื้นฐาน
3. การสร้างแอพพลิเคชันใน Django
4. การ Activate แอพพลิเคชั่นใน settings.py
5. การสร้างโมเดลใน Django
6. การสร้างและประยุกต์ทำงานกับ model migration
7. การสร้าง admin site สำหรับ model

##### #1. การสร้างโปรเจ็กต์ Django

\#1.1 activate virtual environment บน windows
```bash
env\Scripts\activate
```

\#1.2 สร้างโปรเจ็กต์ Django ในโฟลเดอร์ DjangoAGC บน macOS and Linux and Windows
```bash
django-admin startproject mysite
```

\#1.3 เปิดโปรเจ็กต์ mysite เข้า vscode
```bash
code mysite -r
```

\#1.4 โครงสร้างโปรเจ็กต์ในตอนนี้
```bash
mysite
├── manage.py
└── mysite
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

##### #2. การ migrate ฐานข้อมูลเริ่มต้น

```bash
python manage.py migrate
```

\#2.1 ทดสอบ runserver
```bash
python manage.py runserver
```

##### #3. การสร้างแอพพลิเคชันใน Django

\#3.1 สร้างแอพพลิเคชัน blog ในโปรเจ็กต์ mysite
```bash
python manage.py startapp blog
```

\#3.2 โครงสร้างโปรเจ็กต์ในตอนนี้
```bash
mysite # โปรเจ็กต์ mysite
├── blog # สร้างแอพพลิเคชัน blog
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── manage.py
└── mysite # โปรเจ็กต์ mysite
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
    db.sqlite3 # ฐานข้อมูลเริ่มต้น
```

##### #4. Activate แอพพลิเคชัน blog ในไฟล์ mysite/settings.py
```python
INSTALLED_APPS = [
    ...
    'blog.apps.BlogConfig', # แอพพลิเคชัน blog
]
```

##### #5. การสร้างโมเดลใน Django

\#5.1 แก้ไขไฟล์ blog/models.py
```python
from django.db import models

# สร้างโมเดล Post
class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()

    def __str__(self):
        return self.title
```
\#5.2 เพิ่ม datetime ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone # เพิ่ม datetime

# สร้างโมเดล Post
class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now) # เพิ่ม datetime
    created = models.DateTimeField(auto_now_add=True) # เพิ่ม datetime
    updated = models.DateTimeField(auto_now=True) # เพิ่ม datetime

    def __str__(self):
        return self.title
```

\#5.3 การกำหนดการเรียงข้อมูลในโมเดล Post ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now)
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)

    class Meta: # การกำหนดการเรียงข้อมูลในโมเดล Post
        ordering = ['-publish'] # เรียงลำดับโพสต์จากวันที่ล่าสุดไปยังเก่าสุด

    def __str__(self):
        return self.title
```

\#5.4 การเพิ่ม index ในโมเดล Post ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now)
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']), # เพิ่ม index
        ]

    def __str__(self):
        return self.title
```

\#5.5 เพิ่มฟิลด์ status ในโมเดล Post ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):

    class Status(models.TextChoices): # เพิ่มฟิลด์ status
        DRAFT = 'DF', 'Draft'
        PUBLISHED = 'PB', 'Published'
    
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now)
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)
    status = models.CharField(max_length=2, 
                                choices=Status.choices, 
                                default=Status.DRAFT) # เพิ่มฟิลด์ status

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']),
        ]

    def __str__(self):
        return self.title
```
\#5.6 ทดสอบเรียกดู status ผ่าน shell
```bash
python manage.py shell
```
```python
from blog.models import Post
Post.Status.choices
Post.Status.labels
Post.Status.values
Post.Status.names
```

\#5.7 สร้างความสัมพันธ์ในโมเดล Post กับ User ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone
from django.contrib.auth.models import User # เพิ่มความสัมพันธ์กับ User

class Post(models.Model):
    ...
    author = models.ForeignKey(User, 
                                on_delete=models.CASCADE, 
                                related_name='blog_posts') # เพิ่มความสัมพันธ์กับ User

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']),
        ]

    def __str__(self):
        return self.title
```

##### #6. การสร้างไฟล์ migrations และ migrate ฐานข้อมูล
\#6.1 สร้างไฟล์ migrations ในโมเดล blog
```bash
python manage.py makemigrations blog
```

\#6.2 เรียกดูไฟล์ migrations ในโมเดล blog
```bash
python manage.py sqlmigrate blog 0001
```

\#6.3 ทำการ migrate ฐานข้อมูล
```bash
python manage.py migrate
```

##### #7. การสร้าง admin site สำหรับ model
\#7.1 สร้าง superuser
```bash
python manage.py createsuperuser
```

\#7.2 ทดสอบเข้า admin site
```bash
python manage.py runserver
```
เข้า admin site ที่ http://127.0.0.1:8000/admin

\#7.3 เพิ่มโมเดล Post ในไฟล์ blog/admin.py
```python
from django.contrib import admin
from .models import Post

# Register your models here.
admin.site.register(Post)
```


