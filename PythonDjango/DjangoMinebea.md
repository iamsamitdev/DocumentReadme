## Django MVC for Minebea
---
## ⚡ Day 1

### 1 ดาวน์โหลดเอกสารประกอบการเรียนรู้
- [ ] [Django MVC for Minibea](https://bit.ly/django-minebea)

### 2 Tools & Environment Setup
- [ ] [Python 3.13.x](https://www.python.org/downloads/)
- [ ] [NodeJS 22.x.x](https://nodejs.org/en/download)
- [ ] [Visual Studio Code](https://code.visualstudio.com/download)
- [ ] [Git](https://git-scm.com/downloads)

### 3 ตรวจสอบเวอร์ชั่นของแต่ละเครื่องมือ
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
- Prettier - Code formatter by Prettier
- SQLite Viewer by Florian Klampfer
- Postman by Postman
- MDX by unified
- MDX Preview by Xiaoyi Chen
- One Dark Pro by binaryify
```
### 4. การสร้าง Virtual Enviroment
\#4.1 Windows
```bash
mkdir django_minebea/firstdjango
cd django_minebea/firstdjango

python -m venv env
```

\#4.2 Mac OS and Linux
```bash
mkdir django_minebea/firstdjango
cd django_minebea/firstdjango

python3 -m venv env
```

### 5. การเปิดใช้งาน Virtual Enviroment
\#5.1 Windows
```bash
env\Scripts\activate
```

\#5.2 Mac OS and Linux
```bash
source env/bin/activate
```

### 6. การติดตั้ง Django
\#6.1 ติดตั้ง Django 5.2.5
```bash
pip install django==5.2.5
```
\#6.2 เช็ครายการ Package ที่ติดตั้งแล้ว
```bash
pip list
```

### 7. การสร้าง Project ใน Django
```bash
django-admin startproject firstdjango .
```

### 8. การรันโปรแกรม Django
\#8.1 รันโปรแกรม Django
```bash
python manage.py runserver
```
or run with port 8110
```bash
python manage.py runserver 8110
```

### 9. เรียนรู้ Django Project Structure
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

### 10. การสร้าง View ใน Django
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

def home(request):
    return HttpResponse("Welcome to Django Minebea")
```

\#10.5 แก้ไขไฟล์ urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
    path('admin/', admin.site.urls),
]
```

### 11. การกำหนด Path แบบมี Parameter
\#11.1 แก้ไขไฟล์ views.py
```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Welcome to Django Minebea")


def about(request):
    return HttpResponse("About Page")


# fucntion แบบมี parameter
def search(request, keyword, page):
    return HttpResponse(f'Search for: {keyword} page: {page}')


# function แบบมี query string
def maps(request):
    type = request.GET.get('type', 'hybrid')
    lat = request.GET.get('lat', '13.7245601')
    lon = request.GET.get('lon', '100.4930241')
    zoom = request.GET.get('z', 11)

    return HttpResponse(f"Map type: {type} <br> \
        Location: {lat},{lon}<br> \
        Zoom: {zoom}")
```

\#11.2 แก้ไขไฟล์ urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [

    path('', views.home, name='home'),
    path('about', views.about, name='about'),

    # path แบบมี parameter เช่น keyword และ page
    # ตัวอย่างเช่น /search/django/5
    path('search/<str:keyword>/<int:page>', views.search, name='search'),
    path('admin/', admin.site.urls),
    
    # path แบบมี query string
    # ตัวอย่างเช่น /maps?type=satellite&lat=13.387378&lon=100.038930&z=17
    path('maps', views.maps, name='maps'),
]
```

### 12. การสร้าง Template ใน Django
\#12.1 สร้างโฟลเดอร์ templates ในโปรเจคบน Windows, macOS and Linux
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
    <title>Django Minebea</title>
</head>
<body>
    <h1>Welcome to Django Minebea</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Consequatur, commodi recusandae? Hic est sint in eos minus quidem illo aliquam, quae modi, molestiae amet unde, harum quasi aliquid assumenda veritatis!</p>
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

### 13. การสร้าง Static File ใน Django
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
    <title>Django Minebea</title>
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
</head>
<body>
    <h1>Welcome to Django Minebea</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Consequatur, commodi recusandae? Hic est sint in eos minus quidem illo aliquam, quae modi, molestiae amet unde, harum quasi aliquid assumenda veritatis!</p>
</body>
</html>
```

\#13.6 การใส่รูปภาพในโปรเจ็กต์ที่ path /static/images/mypic.png
```bash
mkdir static/images
```

\#13.7 คัดลอกไฟล์ moodeng.jpg ไปยังโฟลเดอร์ static/images
```bash
cp moodeng.jpg static/images
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
    <h1>Welcome to Django Minebea</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Consequatur, commodi recusandae? Hic est sint in eos minus quidem illo aliquam, quae modi, molestiae amet unde, harum quasi aliquid assumenda veritatis!</p>
    <img src="{% static '/images/moodeng.jpg' %}" alt="My Picture">
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
│       └── moodeng.jpg
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
    data = {'title': 'Django Minebea', 'message': 'Welcome to Django Minebea'}

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

### 14. การสร้าง app ใน Django
```bash
python manage.py startapp blog
```

\#14.1 แก้ไขไฟล์ settings.py
```python
INSTALLED_APPS = [
    ...
    'blog',
]
```

\#14.2 แก้ไขไฟล์ urls.py ใน blog
```python
from django.urls import path
from blog import views

urlpatterns = [
    path('', views.blog_list, name='blog_list'),

]
```

\#14.3 แก้ไขไฟล์ views.py ใน blog
```python
from django.shortcuts import render


def blog_list(request):
    return render(request, 'blog/list.html')
```

\#14.4 สร้างไฟล์ list.html ในโฟลเดอร์ templates/blog
```bash
mkdir templates/blog
touch templates/blog/list.html
```

\#14.5 แก้ไขไฟล์ list.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Blog List</title>
</head>
<body>
    <h1>Blog List</h1>
    <ul>
        <li><a href="#">Blog Post 1</a></li>
        <li><a href="#">Blog Post 2</a></li>
        <li><a href="#">Blog Post 3</a></li>
    </ul>
</body>
</html>
```

\#14.6 แก้ไขไฟล์ urls.py ใน firstdjango
```python
from django.urls import path, include

urlpatterns = [
    ...
    path('blog/', include('blog.urls')),
]
```

\#14.7 ทดสอบการเข้าถึงบล็อก
```bash
python manage.py runserver
```
เปิดเว็บเบราว์เซอร์และไปที่ <http://127.0.0.1:8000/blog/> เพื่อดูรายการบล็อก

\#14.8 โครงสร้างโปรเจ็กต์ในตอนนี้
```bash
firstdjango
├── firstdjango
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── blog
│   ├── migrations
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── manage.py
├── static
│   ├── css
│   │   └── style.css
│   └── images
│       └── moodeng.jpg
└── templates
    ├── blog
    │   └── list.html
    ├── index.html
    └── test.html
```
### 15. การสร้าง model ใน Django

\#15.1 แก้ไขไฟล์ models.py ใน blog
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now) # timezone.now คือ ฟังก์ชันที่คืนค่าเวลาปัจจุบัน
    created = models.DateTimeField(auto_now_add=True) # auto_now_add คือ สร้างและบันทึกเวลาอัตโนมัติเมื่อสร้าง
    updated = models.DateTimeField(auto_now=True) # auto_now คือ บันทึกเวลาอัตโนมัติเมื่อมีการแก้ไข

    # เมธอด __str__ สำหรับแสดงชื่อเรื่องของโพสต์ในหน้า Admin
    def __str__(self):
        return self.title
```

\#15.2 การกำหนดการเรียงข้อมูลในโมเดล Post ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now) # timezone.now คือ ฟังก์ชันที่คืนค่าเวลาปัจจุบัน
    created = models.DateTimeField(auto_now_add=True) # auto_now_add คือ สร้างและบันทึกเวลาอัตโนมัติเมื่อสร้าง
    updated = models.DateTimeField(auto_now=True) # auto_now คือ บันทึกเวลาอัตโนมัติเมื่อมีการแก้ไข

    class Meta: # การกำหนดการเรียงข้อมูลในโมเดล Post
        ordering = ['-publish'] # เรียงลำดับโพสต์จากวันที่ล่าสุดไปยังเก่าสุด

    # เมธอด __str__ สำหรับแสดงชื่อเรื่องของโพสต์ในหน้า Admin
    def __str__(self):
        return self.title
``` 

\#15.3 การเพิ่ม index ในโมเดล Post ในไฟล์ blog/models.py
```python
from django.db import models
from django.utils import timezone

class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now) # timezone.now คือ ฟังก์ชันที่คืนค่าเวลาปัจจุบัน
    created = models.DateTimeField(auto_now_add=True) # auto_now_add คือ สร้างและบันทึกเวลาอัตโนมัติเมื่อสร้าง
    updated = models.DateTimeField(auto_now=True) # auto_now คือ บันทึกเวลาอัตโนมัติเมื่อมีการแก้ไข

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']), # เพิ่ม index
        ]

    # เมธอด __str__ สำหรับแสดงชื่อเรื่องของโพสต์ในหน้า Admin
    def __str__(self):
        return self.title
``` 

\#15.4 เพิ่มฟิลด์ status ในโมเดล Post ในไฟล์ blog/models.py
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
    publish = models.DateTimeField(default=timezone.now) # timezone.now คือ ฟังก์ชันที่คืนค่าเวลาปัจจุบัน
    created = models.DateTimeField(auto_now_add=True) # auto_now_add คือ สร้างและบันทึกเวลาอัตโนมัติเมื่อสร้าง
    updated = models.DateTimeField(auto_now=True) # auto_now คือ บันทึกเวลาอัตโนมัติเมื่อมีการแก้ไข
    status = models.CharField(max_length=2, 
                                choices=Status.choices, 
                                default=Status.DRAFT) # เพิ่มฟิลด์ status

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']), # เพิ่ม index
        ]

    # เมธอด __str__ สำหรับแสดงชื่อเรื่องของโพสต์ในหน้า Admin
    def __str__(self):
        return self.title
``` 

\#15.5 สร้าง Model Manager สำหรับโพสต์ที่เผยแพร่แล้ว
```python
from django.db import models
from django.utils import timezone
from django.contrib.auth.models import User # เพิ่มความสัมพันธ์กับ User

# สร้าง Model Manager สำหรับโพสต์ที่เผยแพร่แล้ว
class PublishedManager(models.Manager):
    def get_queryset(self):
        return super().get_queryset().filter(status=Post.Status.PUBLISHED)

class Post(models.Model):

    class Status(models.TextChoices): # เพิ่มฟิลด์ status
        DRAFT = 'DF', 'Draft'
        PUBLISHED = 'PB', 'Published'

    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()
    publish = models.DateTimeField(default=timezone.now) # timezone.now คือ ฟังก์ชันที่คืนค่าเวลาปัจจุบัน
    created = models.DateTimeField(auto_now_add=True) # auto_now_add คือ สร้างและบันทึกเวลาอัตโนมัติเมื่อสร้าง
    updated = models.DateTimeField(auto_now=True) # auto_now คือ บันทึกเวลาอัตโนมัติเมื่อมีการแก้ไข
    status = models.CharField(max_length=2, 
                                choices=Status.choices, 
                                default=Status.DRAFT) # เพิ่มฟิลด์ status
    author = models.ForeignKey(User, 
                                on_delete=models.CASCADE, 
                                related_name='blog_posts') # เพิ่มความสัมพันธ์กับ User

    objects = models.Manager() # The default manager.
    published = PublishedManager() # Our custom manager.

    class Meta:
        ordering = ['-publish']
        indexes = [
            models.Index(fields=['-publish']), # เพิ่ม index
        ]

    # เมธอด __str__ สำหรับแสดงชื่อเรื่องของโพสต์ในหน้า Admin
    def __str__(self):
        return self.title
``` 

\#15.6 ทดสอบเรียกดู status ผ่าน shell
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

\#15.7 สร้างความสัมพันธ์ในโมเดล Post กับ User ในไฟล์ blog/models.py
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

### 16. การสร้างไฟล์ migrations และ migrate ฐานข้อมูล
\#16.1 สร้างไฟล์ migrations ในโมเดล blog
```bash
python manage.py makemigrations
```

\#16.2 ทำการ migrate ฐานข้อมูล
```bash
python manage.py migrate
```

### 17. การสร้าง admin site สำหรับ model
\#17.1 สร้าง superuser
```bash
python manage.py createsuperuser

# กรอกข้อมูลผู้ใช้
Username (leave blank to use 'samit'): admin
Email address: admin@email.com
Password: ********
Password (again): ********
Bypass password validation and create user anyway? [y/N]: y
```

\#17.2 ทดสอบเข้า admin site
```bash
python manage.py runserver
```
เข้า admin site ที่ http://127.0.0.1:8000/admin

\#17.3 เพิ่มโมเดล Post ในไฟล์ blog/admin.py
```python
from django.contrib import admin
from .models import Post

# Register your models here.
admin.site.register(Post)
```

### 18. แก้ไข views.py ใน blog สร้างฟังก์ชันสำหรับแสดงโพสต์ทั้งหมด
```python
from django.shortcuts import render
# Import the Post model
from .models import Post

def post_list(request):

    # สร้างตัวแปร posts เก็บโพสต์ทั้งหมดที่มีสถานะเผยแพร่
    posts = Post.published.all() # ใช้โมเดล Post และ Manager published

    # สร้างตัวแปรกำหนดจำนวนโพสต์ที่แสดงต่อหน้า
    per_page = 5
    paginator = Paginator(posts, per_page)
    page = request.GET.get('page')

    try:
        posts = paginator.page(page)
    except PageNotAnInteger:
        posts = paginator.page(1)
    except EmptyPage:
        posts = paginator.page(paginator.num_pages)

    # ส่งค่าตัวแปร posts ไปแสดงผลที่เทมเพลต blog/post/list.html
    return render(request, 'blog/post/list.html', {'posts': posts})
```

### 19. เพิ่มไฟล์ base.html ในโฟลเดอร์ templates/blog
```bash
{% load static %}
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>{% block title %}{% endblock %}</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
  </head>
  <body>

    <nav class="navbar navbar-expand-md navbar-dark bg-dark mb-4">
        <div class="container">
        <a class="navbar-brand" href="{% url 'blog:post_list' %}">BlogNull</a>
        <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse" data-bs-target="#collapsibleNavId" aria-controls="collapsibleNavId"
          aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="collapsibleNavId">
          <ul class="navbar-nav me-auto mt-2 mt-lg-0">
            <li class="nav-item">
              <a class="nav-link active" href="#" aria-current="page">Home <span class="visually-hidden">(current)</span></a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" id="dropdownId" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Dropdown</a>
              <div class="dropdown-menu" aria-labelledby="dropdownId">
                <a class="dropdown-item" href="#">Action 1</a>
                <a class="dropdown-item" href="#">Action 2</a>
              </div>
            </li>
          </ul>
          <form class="d-flex my-2 my-lg-0">
            <input class="form-control me-sm-2" type="text" placeholder="Search">
            <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
          </form>
        </div>
      </div>
    </nav>
    

    <div class="container">
        {% block content %}
        {% endblock %}
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
  </body>
</html>
```

### 19. แก้ไข list.html ใน blog สร้าง path สำหรับแสดงโพสต์ทั้งหมด
```python
{% extends "blog/base.html" %} 
{% block title %}My Blog{% endblock %}
    
{% block content %}
    {% for post in posts %}
        <div class="card mb-4">
            <div class="card-header bg-primary text-white">
                <a href="{% url 'blog:post_detail' post.id %}" class="text-white text-decoration-none"><h5 class="card-title mt-2">{{ post.title }}</h5></a>
            </div>
            <div class="card-body">
                <p class="card-subtitle mb-3 text-body-secondary">{{ post.publish }} By {{ post.author }}</p>
                {{ post.body | truncatewords:30 | linebreaks }}
            </div>
        </div>
    {% endfor %}

    <nav aria-label="Page navigation">
      <ul class="pagination">
        {% if posts.has_previous %}
            <li class="page-item">
                <a class="page-link" href="?page={{ posts.previous_page_number }}" aria-label="Previous">
                    <span aria-hidden="true">&laquo;</span>
                </a>
            </li>
        {% endif %}

        {% for i in posts.paginator.page_range %}
            {% if posts.number == i %}
            <li class="page-item active">
                <a class="page-link" href="#">{{ posts.number }}</a>
            </li>
            {% else %}
            <li class="page-item">
                <a class="page-link" href="?page={{ i }}">{{ i }}</a>
            </li>
            {% endif %}
        {% endfor %}

        {% if posts.has_next %}
            <li class="page-item">
            <a class="page-link" href="?page={{ posts.next_page_number }}" aria-label="Next">
                <span aria-hidden="true">&raquo;</span>
            </a>
            </li>
        {% endif %}

      </ul>
    </nav>

{% endblock %}