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

### ⚡ Day 3

#### Build an Inventory Management System

##### หัวข้อการเรียนรู้
1. การติดตั้งฐานข้อมูล MySQL ผ่าน XAMPP
2. ดาวน์โหลด Template Bootstrap 4 จาก Start Bootstrap
3. การสร้างโปรเจ็กต์ Django ชื่อ inventory
4. การสร้างแอพพลิเคชันใน Django ชื่อ stock
5. การ Activate แอพพลิเคชั่นใน settings.py
6. ปรับโครงสร้างโปรเจ็กต์ Django ใช้ Template Bootstrap 4


##### #1. การติดตั้งฐานข้อมูล MySQL ผ่าน XAMPP

\#1.1 ดาวน์โหลด XAMPP จาก https://www.apachefriends.org/download.html

\#1.2 ติดตั้ง XAMPP และเปิดใช้งาน Apache และ MySQL

\#1.3 เข้าใช้งาน phpMyAdmin ที่ http://localhost/phpmyadmin/

\#1.4 สร้างฐานข้อมูลชื่อ djangoinventory

##### #2. ดาวน์โหลด Template Bootstrap 4 จาก Start Bootstrap

\#2.1 ดาวน์โหลด Template Bootstrap 4 จาก https://startbootstrap.com/themes/sb-admin-2/

\#2.2 แตกไฟล์ sb-admin-2.zip และนำไปไว้ที่โฟลเดอร์ inventory/templates/

##### #3. การสร้างโปรเจ็กต์ Django

\#3.1 สร้าง environment ชื่อ myenv
```bash
python -m venv myenv
```

\#3.2 Activate environment
```bash
myenv\Scripts\activate
```

\#3.3 ติดตั้ง Django 4.1.7
```bash
pip install django==4.1.7
```

\#3.4 ติดตั้ง mysqlclient 2.1.1
```bash
pip install mysqlclient==2.1.1
```

\#3.5 สร้างโปรเจ็กต์ Django ชื่อ inventory
```bash
django-admin startproject inventory
```

##### #4. การสร้างแอพพลิเคชันใน Django ชื่อ stock

\#4.1 สร้างแอพพลิเคชันใน Django ชื่อ stock
```bash
python manage.py startapp stock
```

##### #5. การ Activate แอพพลิเคชั่นใน settings.py

\#5.1 แก้ไขไฟล์ inventory/settings.py
```python
INSTALLED_APPS = [
    ...
    'stock.apps.StockConfig', # เพิ่มแอพพลิเคชั่น stock
]
```

\#5.2 แก้ไข Timezone ในไฟล์ inventory/settings.py
```python
TIME_ZONE = 'Asia/Bangkok'
```

\#5.3 แก้ไข template ในไฟล์ inventory/settings.py
```python
import os

TEMPLATES = [
    {
        ...
        'DIRS': [os.path.join(BASE_DIR, 'templates')], # เพิ่ม template
        ...
    },
]
```

\#5.4 แก้ไข static ในไฟล์ inventory/settings.py
```python
STATIC_URL = '/static/'

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'), # เพิ่ม static
]
```

\#5.5 แก้ไข Database Connection ในไฟล์ inventory/settings.py
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'djangoinventory',
        'USER': 'root',
        'PASSWORD': '',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

##### #6. ปรับโครงสร้างโปรเจ็กต์ Django ใช้ Template Bootstrap 4

\#6.1 แก้ไขไฟล์ inventory/urls.py
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('stock.urls'))
]
```

\#6.2 แก้ไขไฟล์ stock/urls.py
```python
from django import views
from django.urls import path
from . import views

urlpatterns = [
    # Frontend
    path('', views.index, name='index'),

    # Authentication
    path('register', views.register, name='register'),
    path('login', views.login, name='login'),

    # Backend
]
```

\#6.3 แก้ไขไฟล์ stock/views.py
```python
from django.shortcuts import render

# สร้างฟังก์ชันเรียกหน้า html ที่เราสร้างขึ้นมา
def index(request):
    return render(request, 'frontend/index.html')

# ฟังก์ชันเรียกหน้า login.html
def login(request):
    return render(request, 'auth/login.html')

```

\#6.4 สร้างไฟล์ main_layout.html ในโฟลเดอร์ inventory/templates/frontend/
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}{% endblock %}</title>

     <!--  Bootstrap  -->
     <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">

     <!-- Google Font -->
     <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@300;400;500;600&display=swap" rel="stylesheet">

    <!-- Custom CSS -->
    <link href="{% static 'css/style.css' %}" rel="stylesheet">
</head>
<body>
    
    <!-- Menu -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <div class="container">
          <a class="navbar-brand" href="{% url 'index' %}">Inventory</a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <a class="nav-link" href="{% url 'index' %}">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">About</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Register</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="{% url 'login' %}">Login</a>
              </li>
            </ul>
            <form class="d-flex" role="search">
              <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-warning" type="submit">Search</button>
            </form>
          </div>
        </div>
    </nav>

    <!-- Content -->
    {% block content %}{% endblock %}

    <!-- Footer -->
    <div class="container">
        <footer class="py-5">
          <div class="row">
            <div class="col-6 col-md-2 mb-3">
              <h5>Section</h5>
              <ul class="nav flex-column">
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Home</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Features</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Pricing</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">FAQs</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">About</a></li>
              </ul>
            </div>
      
            <div class="col-6 col-md-2 mb-3">
              <h5>Section</h5>
              <ul class="nav flex-column">
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Home</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Features</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Pricing</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">FAQs</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">About</a></li>
              </ul>
            </div>
      
            <div class="col-6 col-md-2 mb-3">
              <h5>Section</h5>
              <ul class="nav flex-column">
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Home</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Features</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">Pricing</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">FAQs</a></li>
                <li class="nav-item mb-2"><a href="#" class="nav-link p-0 text-body-secondary">About</a></li>
              </ul>
            </div>
      
            <div class="col-md-5 offset-md-1 mb-3">
              <form>
                <h5>Subscribe to our newsletter</h5>
                <p>Monthly digest of what's new and exciting from us.</p>
                <div class="d-flex flex-column flex-sm-row w-100 gap-2">
                  <label for="newsletter1" class="visually-hidden">Email address</label>
                  <input id="newsletter1" type="text" class="form-control" placeholder="Email address">
                  <button class="btn btn-primary" type="button">Subscribe</button>
                </div>
              </form>
            </div>
          </div>
      
          <div class="d-flex flex-column flex-sm-row justify-content-between py-4 my-4 border-top">
            <p>© 2023 Company, Inc. All rights reserved.</p>
            <ul class="list-unstyled d-flex">
              <li class="ms-3"><a class="link-body-emphasis" href="#"><svg class="bi" width="24" height="24"><use xlink:href="#twitter"></use></svg></a></li>
              <li class="ms-3"><a class="link-body-emphasis" href="#"><svg class="bi" width="24" height="24"><use xlink:href="#instagram"></use></svg></a></li>
              <li class="ms-3"><a class="link-body-emphasis" href="#"><svg class="bi" width="24" height="24"><use xlink:href="#facebook"></use></svg></a></li>
            </ul>
          </div>
        </footer>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-geWF76RCwLtnZ8qwWowPQNguL3RmwHVBC9FhGdlKrxdiJJigb/j/68SIy3Te4Bkz" crossorigin="anonymous"></script>
</body>
</html>

```

\#6.5 สร้างไฟล์ style.css ในโฟลเดอร์ static/css/
```css
body {
    font-family: 'IBM Plex Sans Thai', sans-serif;
}
```

\#6.6 สร้างไฟล์ index.html ในโฟลเดอร์ inventory/templates/frontend/
```html
{% extends 'frontend/main_layout.html' %}
{% load static %}

{% block content %}
    <!-- Slide -->
    <div id="carouselId" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-indicators">
            <li data-bs-target="#carouselId" data-bs-slide-to="0" class="active" aria-current="true" aria-label="First slide"></li>
            <li data-bs-target="#carouselId" data-bs-slide-to="1" aria-label="Second slide"></li>
            <li data-bs-target="#carouselId" data-bs-slide-to="2" aria-label="Third slide"></li>
        </div>
        <div class="carousel-inner" role="listbox">
            <div class="carousel-item active">
                <img src="{% static '/images/slide1.jpg' %}" class="w-100 d-block" alt="First slide">
            </div>
            <div class="carousel-item">
                <img src="{% static '/images/slide2.jpg' %}" class="w-100 d-block" alt="Second slide">
            </div>
            <div class="carousel-item">
                <img src="{% static '/images/slide3.webp' %}" class="w-100 d-block" alt="Third slide">
            </div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselId" data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselId" data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
    </div>

    <div class="container my-4">
        <h3>หน้าแรก</h3>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Odio quo voluptatum id praesentium, corrupti enim ea maxime eum saepe? Ratione nihil amet, rem aliquam eligendi cupiditate assumenda tenetur laudantium beatae ipsam odio eum fugit corrupti labore vitae est explicabo non quidem dolores suscipit eaque nulla optio voluptatibus. Commodi dolores dicta illo. Ad, voluptatum. Dignissimos animi at sit eveniet laborum quidem vero beatae dolorum nam doloremque. Mollitia ab et, atque esse ducimus tempore non tempora nisi voluptatum necessitatibus laborum in velit molestias facere! Error, unde perferendis iure, est beatae aliquam accusantium maiores molestiae numquam harum consequuntur expedita reiciendis ipsa facere ducimus!</p>
    </div>
{% endblock %}

```

\#6.7 สร้างไฟล์ custom.css ในโฟลเดอร์ inventory/static/backend/css/
```css
body {
    font-family: 'Noto Sans Thai', Poppins, sans-serif;
}
```

\#6.8 สร้างไฟล์ main_layout.html ในโฟลเดอร์ inventory/templates/auth/
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>{% block title %}{% endblock %}</title>

         <!-- Custom fonts for this template-->
        <link href="{% static 'backend/vendor/fontawesome-free/css/all.min.css' %}" 
        rel="stylesheet" type="text/css">
     
        <!-- Google Font -->
        <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Thai&family=Nunito+Sans&family=Poppins&display=swap" rel="stylesheet">

        <!-- Custom styles for this template-->
        <link href="{% static 'backend/css/sb-admin-2.css' %}" rel="stylesheet">
        <link href="{% static 'backend/css/custom.css' %}" rel="stylesheet">

    </head>
<body class="bg-gradient-primary">

    <div class="container">
        {% block content %}{% endblock %}
    </div>

     <!-- Bootstrap core JavaScript-->
     <script src="{% static 'backendvendor/jquery/jquery.min.js' %}"></script>
     <script src="{% static 'backendvendor/bootstrap/js/bootstrap.bundle.min.js' %}"></script>
 
     <!-- Core plugin JavaScript-->
     <script src="{% static 'backendvendor/jquery-easing/jquery.easing.min.js' %}"></script>
 
     <!-- Custom scripts for all pages-->
     <script src="{% static 'backendjs/sb-admin-2.min.js' %}"></script>
    
</body>
</html>
```

\#6.9 สร้างไฟล์ login.html ในโฟลเดอร์ inventory/templates/auth/
```html
{% extends 'auth/main_layout.html' %}
{% load static %}

{% block title %} เข้าสู่ระบบ {% endblock %}

{% block content %}

<div class="row justify-content-center">

  <div class="col-xl-10 col-lg-12 col-md-9">

    <div class="card o-hidden border-0 shadow-lg my-5">
      <div class="card-body p-0">
        <!-- Nested Row within Card Body -->
        <div class="row">
          <div class="col-lg-6 d-none d-lg-block bg-login-image"></div>
          <div class="col-lg-6">
            <div class="p-5">
              <div class="text-center">
                <h1 class="h4 text-gray-900 mb-4">เข้าสู่ระบบ</h1>
              </div>

                <div class="alert alert-danger text-center">
                  อีเมล์หรือรหัสผ่านไม่ถูกต้อง
                </div>

              <form class="user" action="/login" method="post">
                <div class="form-group">
                  <input type="text" 
                  class="form-control form-control-user" 
                  id="username" 
                  name ="username" 
                  placeholder="Username">
                </div>
                <div class="form-group">
                  <input type="password" class="form-control form-control-user" 
                  id="password" 
                  name="password"
                  placeholder="Password">
                </div>
                <div class="form-group">
                  <div class="custom-control custom-checkbox small">
                    <input type="checkbox" class="custom-control-input" id="customCheck">
                    <label class="custom-control-label" for="customCheck">จำฉันไว้</label>
                  </div>
                </div>
                <input type="submit" value="เข้าสู่ระบบ" class="btn btn-primary btn-user btn-block" />
              </form>
              <div class="text-center mt-3">
                <hr>
                <a href="{% url 'register' %}">สมัครสมาชิก</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>

</div>

{% endblock %}
```

\#6.10 สร้างไฟล์ register.html ในโฟลเดอร์ inventory/templates/auth/
```html
{% extends 'auth/main_layout.html' %}
{% load static %}
{% block title %} ลงทะเบียน {% endblock %}
{% block content %}

<div class="row justify-content-center">
    <div class="col-xl-10 col-lg-12 col-md-9">

    <div class="card o-hidden border-0 shadow-lg my-5">
    <div class="card-body p-0">
        <!-- Nested Row within Card Body -->
        <div class="row">
            <div class="col-lg-6 d-none d-lg-block bg-register-image"></div>
            <div class="col-lg-6">
                <div class="p-5">
                    <div class="text-center">
                        <h1 class="h4 text-gray-900 mb-4">ลงทะเบียนเข้าใช้งาน</h1>
                    </div>
                    <div class="alert alert-danger text-center">
                        ลงทะเบียนไม่สำเร็จ
                    </div>
                    <form class="user" action="/register" method="post">
                       
                        <div class="form-group">
                            <input type="text" class="form-control form-control-user" id="firstname" placeholder="First Name">
                        </div>

                        <div class="form-group">
                            <input type="text" class="form-control form-control-user" id="lastname" placeholder="Last Name">
                        </div>

                        <div class="form-group">
                            <input type="email" class="form-control form-control-user" id="email" placeholder="Email Address">
                        </div>

                        <div class="form-group">
                            <input type="text" class="form-control form-control-user" id="username" placeholder="Username">
                        </div>
        
                        <div class="form-group">
                            <input type="password" class="form-control form-control-user" id="password" placeholder="Password">
                        </div>
                        
                        <input type="submit" value="ลงทะเบียน" class="btn btn-primary btn-user btn-block" />
                    </form>
                    
                    <div class="text-center mt-4">
                        <hr>
                        <a href="{% url 'login' %}">เป็นสมาชิกอยู่แล้ว ? เข้าสู่ระบบ</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
    </div>
    </div>
</div>

{% endblock %}
```

\#6.11 สร้างไฟล์ navbar.inc.html ในโฟลเดอร์ inventory/templates/backend/
```html
{% load static %}
<nav class="navbar navbar-expand navbar-light bg-white topbar mb-4 static-top shadow">

    <!-- Sidebar Toggle (Topbar) -->
    <button id="sidebarToggleTop" class="btn btn-link d-md-none rounded-circle mr-3">
        <i class="fa fa-bars"></i>
    </button>

    <!-- Topbar Search -->
    <form class="d-none d-sm-inline-block form-inline mr-auto ml-md-3 my-2 my-md-0 mw-100 navbar-search">
        <div class="input-group">
            <input type="text" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
            <div class="input-group-append">
                <button class="btn btn-primary" type="button">
                    <i class="fas fa-search fa-sm"></i>
                </button>
            </div>
        </div>
    </form>

    <!-- Topbar Navbar -->
    <ul class="navbar-nav ml-auto">

        <!-- Nav Item - Search Dropdown (Visible Only XS) -->
        <li class="nav-item dropdown no-arrow d-sm-none">
            <a class="nav-link dropdown-toggle" href="#" id="searchDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                <i class="fas fa-search fa-fw"></i>
            </a>
            <!-- Dropdown - Messages -->
            <div class="dropdown-menu dropdown-menu-right p-3 shadow animated--grow-in" aria-labelledby="searchDropdown">
                <form class="form-inline mr-auto w-100 navbar-search">
                    <div class="input-group">
                        <input type="text" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
                        <div class="input-group-append">
                            <button class="btn btn-primary" type="button">
                                <i class="fas fa-search fa-sm"></i>
                            </button>
                        </div>
                    </div>
                </form>
            </div>
        </li>

        <!-- Nav Item - Alerts -->
        <li class="nav-item dropdown no-arrow mx-1">
            <a class="nav-link dropdown-toggle" href="#" id="alertsDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                <i class="fas fa-bell fa-fw"></i>
                <!-- Counter - Alerts -->
                <span class="badge badge-danger badge-counter">3+</span>
            </a>
            <!-- Dropdown - Alerts -->
            <div class="dropdown-list dropdown-menu dropdown-menu-right shadow animated--grow-in" aria-labelledby="alertsDropdown">
                <h6 class="dropdown-header">
                    Alerts Center
                </h6>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="mr-3">
                        <div class="icon-circle bg-primary">
                            <i class="fas fa-file-alt text-white"></i>
                        </div>
                    </div>
                    <div>
                        <div class="small text-gray-500">December 12, 2019</div>
                        <span class="font-weight-bold">A new monthly report is ready to download!</span>
                    </div>
                </a>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="mr-3">
                        <div class="icon-circle bg-success">
                            <i class="fas fa-donate text-white"></i>
                        </div>
                    </div>
                    <div>
                        <div class="small text-gray-500">December 7, 2019</div>
                        $290.29 has been deposited into your account!
                    </div>
                </a>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="mr-3">
                        <div class="icon-circle bg-warning">
                            <i class="fas fa-exclamation-triangle text-white"></i>
                        </div>
                    </div>
                    <div>
                        <div class="small text-gray-500">December 2, 2019</div>
                        Spending Alert: We've noticed unusually high spending for your account.
                    </div>
                </a>
                <a class="dropdown-item text-center small text-gray-500" href="#">Show All Alerts</a>
            </div>
        </li>

        <!-- Nav Item - Messages -->
        <li class="nav-item dropdown no-arrow mx-1">
            <a class="nav-link dropdown-toggle" href="#" id="messagesDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                <i class="fas fa-envelope fa-fw"></i>
                <!-- Counter - Messages -->
                <span class="badge badge-danger badge-counter">7</span>
            </a>
            <!-- Dropdown - Messages -->
            <div class="dropdown-list dropdown-menu dropdown-menu-right shadow animated--grow-in" aria-labelledby="messagesDropdown">
                <h6 class="dropdown-header">
                    Message Center
                </h6>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="dropdown-list-image mr-3">
                        <img class="rounded-circle" src="{% static 'backend/img/undraw_profile_1.svg' %}" alt="...">
                        <div class="status-indicator bg-success"></div>
                    </div>
                    <div class="font-weight-bold">
                        <div class="text-truncate">
                            Hi there! I am wondering if you can help me with a
                            problem I've been having.
                        </div>
                        <div class="small text-gray-500">Emily Fowler · 58m</div>
                    </div>
                </a>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="dropdown-list-image mr-3">
                        <img class="rounded-circle" src="{% static 'backend/img/undraw_profile_2.svg' %}" alt="...">
                        <div class="status-indicator"></div>
                    </div>
                    <div>
                        <div class="text-truncate">
                            I have the photos that you ordered last month, how
                            would you like them sent to you?
                        </div>
                        <div class="small text-gray-500">Jae Chun · 1d</div>
                    </div>
                </a>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="dropdown-list-image mr-3">
                        <img class="rounded-circle" src="{% static 'backend/img/undraw_profile_3.svg' %}" alt="...">
                        <div class="status-indicator bg-warning"></div>
                    </div>
                    <div>
                        <div class="text-truncate">
                            Last month's report looks great, I am very happy with
                            the progress so far, keep up the good work!
                        </div>
                        <div class="small text-gray-500">Morgan Alvarez · 2d</div>
                    </div>
                </a>
                <a class="dropdown-item d-flex align-items-center" href="#">
                    <div class="dropdown-list-image mr-3">
                        <img class="rounded-circle" src="https://source.unsplash.com/Mv9hjnEUHR4/60x60" alt="...">
                        <div class="status-indicator bg-success"></div>
                    </div>
                    <div>
                        <div class="text-truncate">
                            Am I a good boy? The reason I ask is because someone
                            told me that people say this to all dogs, even if they aren't good...
                        </div>
                        <div class="small text-gray-500">Chicken the Dog · 2w</div>
                    </div>
                </a>
                <a class="dropdown-item text-center small text-gray-500" href="#">Read More Messages</a>
            </div>
        </li>

        <div class="topbar-divider d-none d-sm-block"></div>

        <!-- Nav Item - User Information -->
        <li class="nav-item dropdown no-arrow">
            <a class="nav-link dropdown-toggle" href="#" id="userDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                <span class="mr-2 d-none d-lg-inline text-gray-600 small">Douglas McGee</span>
                <img class="img-profile rounded-circle" src="{% static 'backend/img/undraw_profile.svg' %}">
            </a>
            <!-- Dropdown - User Information -->
            <div class="dropdown-menu dropdown-menu-right shadow animated--grow-in" aria-labelledby="userDropdown">
                <a class="dropdown-item" href="#">
                    <i class="fas fa-user fa-sm fa-fw mr-2 text-gray-400"></i>
                    Profile
                </a>
                <a class="dropdown-item" href="#">
                    <i class="fas fa-cogs fa-sm fa-fw mr-2 text-gray-400"></i>
                    Settings
                </a>
                <a class="dropdown-item" href="#">
                    <i class="fas fa-list fa-sm fa-fw mr-2 text-gray-400"></i>
                    Activity Log
                </a>
                <div class="dropdown-divider"></div>
                <a class="dropdown-item" href="#">
                    <i class="fas fa-sign-out-alt fa-sm fa-fw mr-2 text-gray-400"></i>
                    Logout
                </a>
            </div>
        </li>

    </ul>

</nav>
```

\#6.12 สร้างไฟล์ sidebar.inc.html ในโฟลเดอร์ inventory/templates/backend/
```html
<ul class="navbar-nav sidebar sidebar-dark accordion" id="accordionSidebar">

    <!-- Sidebar - Brand -->
    <a class="sidebar-brand d-flex align-items-center justify-content-center" href="#">
        <div class="sidebar-brand-text mx-3">Inventory</div>
    </a>

    <!-- Divider -->
    <hr class="sidebar-divider my-0">

    <!-- Nav Item - Dashboard -->
    <li class="nav-item">
        <a class="nav-link" href="#">
            <i class="fas fa-fw fa-tachometer-alt"></i>
            <span>Dashboard</span>
        </a>
    </li>

    <!-- Divider -->
    <hr class="sidebar-divider">

    <!-- Heading -->
    <div class="sidebar-heading">
        Manage
    </div>

    <!-- Nav Item - Pages Collapse Menu -->
    <li class="nav-item active">
        <a class="nav-link collapsed" href="#" data-toggle="collapse" data-target="#collapseTwo" aria-expanded="true" aria-controls="collapseTwo">
            <i class="fas fa-fw fa-table"></i>
            <span>Stock</span>
        </a>
        <div id="collapseTwo" class="collapse show" aria-labelledby="headingTwo" data-parent="#accordionSidebar">
            <div class="py-2 collapse-inner rounded">
                <a class="collapse-item" href="#">Products</a>
            </div>
        </div>
    </li>

    <!-- Divider -->
    <hr class="sidebar-divider">

    <!-- Heading -->
    <div class="sidebar-heading">
        System
    </div>

    <!-- Nav Item - Pages Collapse Menu -->
    <li class="nav-item">
        <a class="nav-link collapsed" href="#" data-toggle="collapse" data-target="#collapsePages" aria-expanded="true" aria-controls="collapsePages">
            <i class="fas fa-fw fa-folder"></i>
            <span>Pages</span>
        </a>
        <div id="collapsePages" class="collapse" aria-labelledby="headingPages" data-parent="#accordionSidebar">
            <div class="py-2 collapse-inner rounded">
                <a class="collapse-item" href="#">Login</a>
                <a class="collapse-item" href="#">Register</a>
                <a class="collapse-item" href="#">Forgot Password</a>
            </div>
        </div>
    </li>

    <!-- Nav Item - Charts -->
    <li class="nav-item">
        <a class="nav-link" href="#">
            <i class="fas fa-fw fa-chart-area"></i>
            <span>Charts</span>
        </a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="#">
            <i class="fas fa-fw fa-wrench"></i>
            <span>Settings</span>
        </a>
    </li>
    <!-- Divider -->
    <hr class="sidebar-divider d-none d-md-block">

    <!-- Sidebar Toggler (Sidebar) -->
    <div class="text-center d-none d-md-inline">
        <button class="rounded-circle border-0" id="sidebarToggle"></button>
    </div>

</ul>
```

\#6.13 สร้างไฟล์ footer.inc.html ในโฟลเดอร์ inventory/templates/backend/
```html
<footer class="sticky-footer bg-white">
    <div class="container my-auto">
        <div class="copyright text-center my-auto">
            <span>Copyright © Your Website 2023</span>
        </div>
    </div>
</footer>
```

\#6.14 สร้างไฟล์ main_layout.html ในโฟลเดอร์ inventory/templates/backend/
```html
{% load static %}
<!DOCTYPE html>

<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>{% block title %}{% endblock %} - Inventory System</title>

    <!-- Custom fonts for this template-->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Thai&family=Nunito+Sans&family=Poppins&display=swap" rel="stylesheet">

    <!-- Custom styles for this template-->
    <link rel="stylesheet" href="{% static './backend/css/sb-admin-2.css' %}" />
    <link rel="stylesheet" href="{% static './backend/vendor/fontawesome-free/css/all.css' %}" />
    <link rel="stylesheet" href="{% static './backend/css/custom.css' %}" />

</head>
<body id="page-top">

    <div id="wrapper">

        <!--Sidebar-->
        {% include 'backend/sidebar.inc.html' %}

        <div id="content-wrapper" class="d-flex flex-column">
            <div id="content">
                <!--Navbar-->
                {% include 'backend/navbar.inc.html' %}

                <!--Content-->
                {% block content %}
                {% endblock %}

                {% include 'backend/footer.inc.html' %}
            </div>
        </div>

    </div>

    {% block footer_scripts %}
    <script src="{% static './backend/vendor/jquery/jquery.js' %}"></script>
    <script src="{% static './backend/vendor/bootstrap/js/bootstrap.js' %}"></script>
    <script src="{% static './backend/vendor/jquery-easing/jquery.easing.js' %}"></script>
    <script src="{% static './backend/js/sb-admin-2.js' %}"></script>
    {% endblock footer_scripts %}
</body>
</html>
```

\#6.14 สร้างไฟล์ dashboard.html ในโฟลเดอร์ inventory/templates/backend/
```html
{% extends 'backend/main_layout.html' %}
{% load static %}
{% block title %} แดชบอร์ด {% endblock %}
{% block content %}

<div class="container-fluid">
    <!-- Page Heading -->
    <div class="d-sm-flex align-items-center justify-content-between mb-4">
        <h1 class="h3 mb-0 text-gray-800">แดชบอร์ด</h1>
        <a href="#" class="d-none d-sm-inline-block btn btn-sm btn-primary shadow-sm"><i class="fas fa-download fa-sm text-white-50"></i> Generate Report</a>
    </div>

    <!-- Content Row -->
    <div class="row">

        <!-- Earnings (Monthly) Card Example -->
        <div class="col-xl-3 col-md-6 mb-4">
            <div class="card border-left-primary shadow h-100 py-2">
                <div class="card-body">
                    <div class="row no-gutters align-items-center">
                        <div class="col mr-2">
                            <div class="text-xs font-weight-bold text-primary text-uppercase mb-1">
                                Earnings (Monthly)
                            </div>
                            <div class="h5 mb-0 font-weight-bold text-gray-800">$40,000</div>
                        </div>
                        <div class="col-auto">
                            <i class="fas fa-calendar fa-2x text-gray-300"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Earnings (Monthly) Card Example -->
        <div class="col-xl-3 col-md-6 mb-4">
            <div class="card border-left-success shadow h-100 py-2">
                <div class="card-body">
                    <div class="row no-gutters align-items-center">
                        <div class="col mr-2">
                            <div class="text-xs font-weight-bold text-success text-uppercase mb-1">
                                Earnings (Annual)
                            </div>
                            <div class="h5 mb-0 font-weight-bold text-gray-800">$215,000</div>
                        </div>
                        <div class="col-auto">
                            <i class="fas fa-dollar-sign fa-2x text-gray-300"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Earnings (Monthly) Card Example -->
        <div class="col-xl-3 col-md-6 mb-4">
            <div class="card border-left-info shadow h-100 py-2">
                <div class="card-body">
                    <div class="row no-gutters align-items-center">
                        <div class="col mr-2">
                            <div class="text-xs font-weight-bold text-info text-uppercase mb-1">
                                Tasks
                            </div>
                            <div class="row no-gutters align-items-center">
                                <div class="col-auto">
                                    <div class="h5 mb-0 mr-3 font-weight-bold text-gray-800">50%</div>
                                </div>
                                <div class="col">
                                    <div class="progress progress-sm mr-2">
                                        <div class="progress-bar bg-info" role="progressbar"
                                             style="width: 50%" aria-valuenow="50" aria-valuemin="0"
                                             aria-valuemax="100"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="col-auto">
                            <i class="fas fa-clipboard-list fa-2x text-gray-300"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Pending Requests Card Example -->
        <div class="col-xl-3 col-md-6 mb-4">
            <div class="card border-left-warning shadow h-100 py-2">
                <div class="card-body">
                    <div class="row no-gutters align-items-center">
                        <div class="col mr-2">
                            <div class="text-xs font-weight-bold text-warning text-uppercase mb-1">
                                Pending Requests
                            </div>
                            <div class="h5 mb-0 font-weight-bold text-gray-800">18</div>
                        </div>
                        <div class="col-auto">
                            <i class="fas fa-comments fa-2x text-gray-300"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Content Row -->
    <div class="row">

        <!-- Area Chart -->
        <div class="col-xl-8 col-lg-7">
            <div class="card shadow mb-4">
                <!-- Card Header - Dropdown -->
                <div class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
                    <h6 class="m-0 font-weight-bold text-primary">Earnings Overview</h6>
                    <div class="dropdown no-arrow">
                        <a class="dropdown-toggle" href="#" role="button" id="dropdownMenuLink"
                           data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            <i class="fas fa-ellipsis-v fa-sm fa-fw text-gray-400"></i>
                        </a>
                        <div class="dropdown-menu dropdown-menu-right shadow animated--fade-in"
                             aria-labelledby="dropdownMenuLink">
                            <div class="dropdown-header">Dropdown Header:</div>
                            <a class="dropdown-item" href="#">Action</a>
                            <a class="dropdown-item" href="#">Another action</a>
                            <div class="dropdown-divider"></div>
                            <a class="dropdown-item" href="#">Something else here</a>
                        </div>
                    </div>
                </div>
                <!-- Card Body -->
                <div class="card-body">
                    <div class="chart-area">
                        <canvas id="myAreaChart"></canvas>
                    </div>
                </div>
            </div>
        </div>

        <!-- Pie Chart -->
        <div class="col-xl-4 col-lg-5">
            <div class="card shadow mb-4">
                <!-- Card Header - Dropdown -->
                <div class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
                    <h6 class="m-0 font-weight-bold text-primary">Revenue Sources</h6>
                    <div class="dropdown no-arrow">
                        <a class="dropdown-toggle" href="#" role="button" id="dropdownMenuLink"
                           data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            <i class="fas fa-ellipsis-v fa-sm fa-fw text-gray-400"></i>
                        </a>
                        <div class="dropdown-menu dropdown-menu-right shadow animated--fade-in"
                             aria-labelledby="dropdownMenuLink">
                            <div class="dropdown-header">Dropdown Header:</div>
                            <a class="dropdown-item" href="#">Action</a>
                            <a class="dropdown-item" href="#">Another action</a>
                            <div class="dropdown-divider"></div>
                            <a class="dropdown-item" href="#">Something else here</a>
                        </div>
                    </div>
                </div>
                <!-- Card Body -->
                <div class="card-body">
                    <div class="chart-pie pt-4 pb-2">
                        <canvas id="myPieChart"></canvas>
                    </div>
                    <div class="mt-4 text-center small">
                        <span class="mr-2">
                            <i class="fas fa-circle text-primary"></i> Direct
                        </span>
                        <span class="mr-2">
                            <i class="fas fa-circle text-success"></i> Social
                        </span>
                        <span class="mr-2">
                            <i class="fas fa-circle text-info"></i> Referral
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Content Row -->
    <div class="row">

        <!-- Content Column -->
        <div class="col-lg-6">

            <div class="card shadow mb-4">
                <div class="card-header py-3">
                    <h6 class="m-0 font-weight-bold text-primary">6 Month sale</h6>
                </div>
                <div class="card-body">
                    <div class="chart-bar">
                        <canvas id="myBarChart"></canvas>
                    </div>
                </div>
            </div>

        </div>

        <!-- Content Column -->
        <div class="col-lg-6 mb-4">

            <!-- Project Card Example -->
            <div class="card shadow mb-4">
                <div class="card-header py-3">
                    <h6 class="m-0 font-weight-bold text-primary">Projects</h6>
                </div>
                <div class="card-body">
                    <h4 class="small font-weight-bold">
                        Server Migration <span class="float-right">20%</span>
                    </h4>
                    <div class="progress mb-4">
                        <div class="progress-bar bg-danger" role="progressbar" style="width: 20%"
                             aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                    <h4 class="small font-weight-bold">
                        Sales Tracking <span class="float-right">40%</span>
                    </h4>
                    <div class="progress mb-4">
                        <div class="progress-bar bg-warning" role="progressbar" style="width: 40%"
                             aria-valuenow="40" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                    <h4 class="small font-weight-bold">
                        Customer Database <span class="float-right">60%</span>
                    </h4>
                    <div class="progress mb-4">
                        <div class="progress-bar" role="progressbar" style="width: 60%"
                             aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                    <h4 class="small font-weight-bold">
                        Payout Details <span class="float-right">80%</span>
                    </h4>
                    <div class="progress mb-4">
                        <div class="progress-bar bg-info" role="progressbar" style="width: 80%"
                             aria-valuenow="80" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                    <h4 class="small font-weight-bold">
                        Account Setup <span class="float-right">Complete!</span>
                    </h4>
                    <div class="progress">
                        <div class="progress-bar bg-success" role="progressbar" style="width: 100%"
                             aria-valuenow="100" aria-valuemin="0" aria-valuemax="100"></div>
                    </div>
                </div>
            </div>

        </div>

    </div>

</div>

{% endblock %}

{% block footer_scripts %}
    {{ block.super }}
    <script src="{% static './backend/vendor/chart.js/Chart.min.js' %}"></script>
    <script src="{% static './backend/js/demo/chart-area-demo.js' %}"></script>
    <script src="{% static './backend/js/demo/chart-pie-demo.js' %}"></script>
    <script src="{% static './backend/js/demo/chart-bar-demo.js' %}"></script>
{% endblock footer_scripts %}
```

\#6.15 แก้ไขไฟล์ custom.css ในโฟลเดอร์ inventory/static/backend/css/
```css
body {
    font-family: 'Noto Sans Thai', Poppins, sans-serif;
}

.sidebar .nav-item .nav-link{
    padding: 15px 20px !important;
}

.sidebar .nav-item .nav-link span{
    font-size: 16px !important;
}

.sidebar-dark{
    background-color: #0f172a; /* สีเมนูด้านข้าง */
}

.sidebar .nav-item .collapse .collapse-inner .collapse-item, .sidebar .nav-item .collapsing .collapse-inner .collapse-item{
    color: #ffffff;
    font-size: 16px;
}

.sidebar .nav-item .collapse .collapse-inner .collapse-item:hover, .sidebar .nav-item .collapsing .collapse-inner .collapse-item:hover{
    background-color: #17264b;
}

.sidebar .sidebar-heading{
    font-size: 12px !important;
}

.sidebar .nav-item .collapse{
    background-color: #0f172a;
}
```

\#6.16 แก้ไขไฟล์ views.py ในโฟลเดอร์ stock/
```python
from django.shortcuts import render

# สร้างฟังก์ชันเรียกหน้า html ที่เราสร้างขึ้นมา
def index(request):
    return render(request, 'frontend/index.html')

# ฟังก์ชันเรียกหน้า login.html
def login(request):
    return render(request, 'auth/login.html')

# ฟังก์ชันเรียกหน้า register.html
def register(request):
    return render(request, 'auth/register.html')

# ฟังก์ชันเรียกหน้า dashboard.html
def dashboard(request):
    return render(request, 'backend/dashboard.html')
```

\#6.16 แก้ไขไฟล์ urls.py ในโฟลเดอร์ stock/
```python
from django import views
from django.urls import path
from . import views

urlpatterns = [
    # Frontend
    path('', views.index, name='index'),

    # Authentication
    path('register', views.register, name='register'),
    path('login', views.login, name='login'),

    # Backend
    path('backend/dashboard', views.dashboard, name='dashboard'),
]
```

### ⚡ Day 4

#### CRUD MySQL ด้วย Django

##### หัวข้อการเรียนรู้
1. การสร้างโมเดลสำหรับเก็บข้อมูลสินค้า  
2. การสร้างไฟล์ migrations และ migrate ฐานข้อมูล
3. การสร้าง superuser และเข้า admin site
4. การสร้างหน้าแสดงข้อมูลสินค้า
5. การสร้างหน้าเพิ่มข้อมูลสินค้า
6. การสร้างหน้าแก้ไขข้อมูลสินค้า
7. การสร้างหน้าลบข้อมูลสินค้า

##### #1. การสร้างโมเดลสำหรับเก็บข้อมูลสินค้า

\#1.1 แก้ไขไฟล์ stock/models.py
```python
from django.db import models

# stock product 
class Product(models.Model):
    product_name = models.CharField(max_length=128)
    product_detail = models.TextField()
    product_barcode = models.CharField(max_length=13)
    product_qty = models.IntegerField()
    product_price = models.DecimalField(max_digits=7, decimal_places=2)
    product_image = models.CharField(max_length=128)
    product_status = models.IntegerField()

    def __str__(self):
        return self.product_name
```

##### #2. การสร้างไฟล์ migrations และ migrate ฐานข้อมูล

\#2.1 สร้างไฟล์ migrations และ migrate ฐานข้อมูล
```bash
$ python manage.py makemigrations
$ python manage.py migrate
```

##### #3. การสร้าง superuser และเข้า admin site

\#3.1 สร้าง superuser
```bash
$ python manage.py createsuperuser
```

\#3.2 เข้า admin site โดยใช้ username และ password ที่ได้สร้างไว้
```bash
$ python manage.py runserver
```

##### #4. การสร้างหน้าแสดงข้อมูลสินค้า

\#4.1 แก้ไขไฟล์ stock/views.py
```python

from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'backend/dashboard.html')

def product_list(request):
    return render(request, 'backend/product_list.html')
```

\#4.2 แก้ไขไฟล์ inventory/urls.py
```python
from django.contrib import admin
from django.urls import path
from stock import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index),
    path('product_list/', views.product_list),
]
```

\#4.3 แก้ไขไฟล์ inventory/templates/backend/dashboard.html
```html
{% extends 'base.html' %}

{% block title %}Dashboard{% endblock %}

{% block content %}
    <h1>Dashboard</h1>
    <a href="{% url 'product_list' %}">Product List</a>
{% endblock %}
```

\#4.4 สร้างไฟล์ inventory/templates/backend/product_list.html
```html
{% extends 'base.html' %}

{% block title %}Product List{% endblock %}

{% block content %}
    <h1>Product List</h1>
{% endblock %}
```

##### #5. การสร้างหน้าเพิ่มข้อมูลสินค้า

\#5.1 แก้ไขไฟล์ stock/views.py
```python
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'backend/dashboard.html')

def product_list(request):
    return render(request, 'backend/product_list.html')

def product_add(request):
    return render(request, 'backend/product_add.html')
```

\#5.2 แก้ไขไฟล์ inventory/urls.py
```python
from django.contrib import admin
from django.urls import path
from stock import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index),
    path('product_list/', views.product_list, name='product_list'),
    path('product_add/', views.product_add, name='product_add'),
]
```

\#5.3 แก้ไขไฟล์ inventory/templates/backend/product_list.html
```html
{% extends 'base.html' %}

{% block title %}Product List{% endblock %}

{% block content %}
    <h1>Product List</h1>
    <a href="{% url 'product_add' %}">Add Product</a>
{% endblock %}
```

\#5.4 สร้างไฟล์ inventory/templates/backend/product_add.html
```html
{% extends 'base.html' %}

{% block title %}Add Product{% endblock %}

{% block content %}
    <h1>Add Product</h1>
{% endblock %}
```

##### #6. การสร้างหน้าแก้ไขข้อมูลสินค้า

\#6.1 แก้ไขไฟล์ stock/views.py
```python
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'backend/dashboard.html')

def product_list(request):
    return render(request, 'backend/product_list.html')

def product_add(request):
    return render(request, 'backend/product_add.html')

def product_edit(request):
    return render(request, 'backend/product_edit.html')
```

\#6.2 แก้ไขไฟล์ inventory/urls.py
```python
from django.contrib import admin
from django.urls import path
from stock import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index),
    path('product_list/', views.product_list, name='product_list'),
    path('product_add/', views.product_add, name='product_add'),
    path('product_edit/', views.product_edit, name='product_edit'),
]
```

\#6.3 แก้ไขไฟล์ inventory/templates/backend/product_list.html
```html
{% extends 'base.html' %}

{% block title %}Product List{% endblock %}

{% block content %}
    <h1>Product List</h1>
    <a href="{% url 'product_add' %}">Add Product</a>
    <a href="{% url 'product_edit' %}">Edit Product</a>
{% endblock %}
```

\#6.4 สร้างไฟล์ inventory/templates/backend/product_edit.html
```html
{% extends 'base.html' %}

{% block title %}Edit Product{% endblock %}

{% block content %}
    <h1>Edit Product</h1>
{% endblock %}
```

##### #7. การสร้างหน้าลบข้อมูลสินค้า

\#7.1 แก้ไขไฟล์ stock/views.py
```python
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'backend/dashboard.html')

def product_list(request):
    return render(request, 'backend/product_list.html')

def product_add(request):
    return render(request, 'backend/product_add.html')

def product_edit(request):
    return render(request, 'backend/product_edit.html')

def product_delete(request):
    return render(request, 'backend/product_delete.html')
```

\#7.2 แก้ไขไฟล์ inventory/urls.py
```python
from django.contrib import admin
from django.urls import path
from stock import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index),
    path('product_list/', views.product_list, name='product_list'),
    path('product_add/', views.product_add, name='product_add'),
    path('product_edit/', views.product_edit, name='product_edit'),
    path('product_delete/', views.product_delete, name='product_delete'),
]
```

\#7.3 แก้ไขไฟล์ inventory/templates/backend/product_list.html
```html
{% extends 'base.html' %}

{% block title %}Product List{% endblock %}

{% block content %}
    <h1>Product List</h1>
    <a href="{% url 'product_add' %}">Add Product</a>
    <a href="{% url 'product_edit' %}">Edit Product</a>
    <a href="{% url 'product_delete' %}">Delete Product</a>
{% endblock %}
```

\#7.4 สร้างไฟล์ inventory/templates/backend/product_delete.html
```html
{% extends 'base.html' %}

{% block title %}Delete Product{% endblock %}

{% block content %}
    <h1>Delete Product</h1>
{% endblock %}
```