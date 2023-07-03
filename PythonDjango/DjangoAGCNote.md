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
```bash
from django.http import HttpResponse

def index(request):
    return HttpResponse("Welcome to Django AGC")
```

\#10.5 แก้ไขไฟล์ urls.py
```bash
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
```bash
from django.http import HttpResponse

def index(request):
    return HttpResponse("Welcome to Django AGC")

def hello(request, name):
    return HttpResponse(f"Hello {name}")
```

\#11.2 แก้ไขไฟล์ urls.py
```bash
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

\#12.2 สร้างโฟลเดอร์ templates ในโปรเจคบน Windows
```bash
md templates
```

\#12.3 สร้างไฟล์ index.html ในโฟลเดอร์ templates บน macOS and Linux
```bash
touch templates/index.html
```

\#12.4 สร้างไฟล์ index.html ในโฟลเดอร์ templates บน Windows
```bash
type nul > templates/index.html
```

\#12.5 แก้ไขไฟล์ index.html
```bash
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

\#12.6 แก้ไขไฟล์ views.py
```bash
from django.http import HttpResponse
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```





