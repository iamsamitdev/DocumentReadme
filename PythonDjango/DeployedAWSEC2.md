### Deployed Python Django 4.2 on AWS EC2 / Ubuntu 22.04 LTS
---
##### Step 1: เตรียมโปรเจ็กต์ Python Django 4.2 export requirements.txt
pip freeze > requirements.txt

##### Step 2: push โปรเจ็กต์ไปยัง Github
git add .
git commit -m "deployed"
git push origin main

##### Step 3: สร้าง EC2 ubuntu instance บน AWS
- ใช้ Security Group ที่เปิด port 80, 443, 22
- ใช้ Key Pair ที่เป็น .pem ไฟล์ หรือ
- ใช้ Key Pair ที่เป็น .ppk ไฟล์ โดยใช้ PuTTYgen แปลง .pem ไฟล์ ให้เป็น .ppk ไฟล์ และใช้ PuTTY ในการเชื่อมต่อ
- หรือใช้ EC2 Instance Connect ในการเชื่อมต่อ

##### Step 4: เข้าไปยัง EC2 ubuntu instance ด้วย SSH หรือ EC2 Instance Connect

- เข้าไปยัง EC2 ubuntu instance ด้วย SSH
ssh -i "keypair.pem"

- เข้าไปยัง EC2 ubuntu instance ด้วย EC2 Instance Connect

##### Step 5: update and upgrade ubuntu
sudo apt-get update
sudo apt-get upgrade

##### Step 6: ติดตั้ง mysql 8.0 and create database

- การถอนการติดตั้ง mysql 8.0
sudo apt purge mysql-server*
sudo rm -r /etc/mysql /var/lib/mysql
sudo rm -r /var/log/mysql
sudo apt autoremove

- เช็ค version ของ mysql
mysql --version

- ติดตั้ง mysql 8.0
sudo apt-get install mysql-server

- เช็ค status ของ mysql
sudo service mysql status

- คำสั่ง start, stop, restart mysql
sudo service mysql start
sudo service mysql stop
sudo service mysql restart

- เข้าไปยัง mysql
sudo mysql

- เรียกดู user ทั้งหมด
SELECT user, host, plugin FROM mysql.user;

- กำหนด password ให้กับ root user
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'xxx';

select * from mysql.user where user = 'root';

- Flush privileges
FLUSH PRIVILEGES;

- ออกจาก mysql
exit

- รันคำสั่งนี้เพื่อป้องกันการเข้าถึง mysql โดยไม่ได้ระบุ password
sudo mysql_secure_installation

- เข้าไปยัง mysql ด้วย password
mysql -u root -p

- สร้าง user ใหม่
CREATE USER 'samit'@'localhost' IDENTIFIED BY 'xxx';

- Grant all privileges
GRANT ALL PRIVILEGES ON *.* TO 'samit'@'localhost' WITH GRANT OPTION;

- Flush privileges
FLUSH PRIVILEGES;

- ออกจาก mysql
exit

- เข้าไปยัง mysql ด้วย user ที่สร้าง
mysql -u samit -p

- สร้าง database
CREATE DATABASE harrowgolf;

- ออกจาก mysql
exit

##### Step 7: Config django project settings.py mysql connection
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'harrowgolf',
        'USER': 'samit',
        'PASSWORD': 'xxx',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}

##### Step 8: ตรวจสอบ python version
python3 --version

##### Step 9: ติดตั้ง python3-venv, python3-pip, python3-dev, libmysqlclient-dev, build-essential
sudo apt-get install python3-venv python3-pip python3-dev default-libmysqlclient-dev build-essential

##### Step 10: สร้าง virtual environment
python3 -m venv env

##### Step 11: เปิดใช้งาน virtual environment
source env/bin/activate

##### Step 12: clone django โปรเจ็กต์จาก github
git clone https://github.com/iamsamitdev/harrowgolf_dj.git

##### Step 13: เข้าไปยังโปรเจ็กต์
cd harrowgolf_dj/harrowgolf

##### Step 14: สร้าง .env และเพิ่ม SECRET_KEY , DEBUG , ALLOWED_HOSTS , DB_ENGINE , DB_HOST , DB_PORT , DB_NAME , DB_USER , DB_PASS

- คำสั่งในการสร้าง .env
sudo nano .env

- ตัวอย่าง .env
SECRET_KEY=django-insecure-g67u&%gp)_zm4_4s)sy(bs4l@j^i&4i+2(rk7&-f)1*28n%52s
DEBUG=True
ALLOWED_HOSTS=*
DB_ENGINE=django.db.backends.mysql
DB_HOST=localhost
DB_PORT=3306
DB_NAME=harrowgolf
DB_USER=samit
DB_PASS=xxx

##### Step 15: ติดตั้ง requirements.txt
pip install -r requirements.txt

##### Step 16: ตรวจสอบ django version และ lib ที่ install ใน virtual environment
pip list

##### Step 17: ติดตั้ง nginx
sudo apt-get install -y nginx

- ทดสอบเข้าไปยัง ip address ของ EC2 instance ด้วย web browser
http://xx.xxx.xxx.xx/

##### Step 18: ติดตั้ง gunicorn
pip install gunicorn

##### Step 19: ติดตั้ง supervisor
sudo apt-get install supervisor

##### Step 20: สร้างไฟล์ supervisor config
sudo nano /etc/supervisor/conf.d/gunicorn.conf

[program:gunicorn]
directory=/home/ubuntu/harrowgolf_dj/harrowgolf
command=/home/ubuntu/env/bin/gunicorn --workers 3 --bind unix:/home/ubuntu/harrowgolf_dj/harrowgolf/app.sock harrowgolf.wsgi:application  
autostart=true
autorestart=true
stderr_logfile=/var/log/gunicorn/gunicorn.err.log
stdout_logfile=/var/log/gunicorn/gunicorn.out.log

[group:guni]
programs:gunicorn

##### Step 21: สร้างไฟล์ log ของ gunicorn
sudo mkdir /var/log/gunicorn

##### Step 22: รีโหลด supervisor
cd /etc/supervisor/conf.d
sudo supervisorctl reread
sudo supervisorctl update

##### Step 23: ตรวจสอบ status ของ gunicorn
sudo supervisorctl status

##### Step 24: แก้ไขไฟล์ nginx.conf
sudo nano /etc/nginx/nginx.conf

แก้ไขไฟล์ nginx.conf ดังนี้
user root;

##### Step 25: สร้างไฟล์ sites-available/django.conf
sudo nano /etc/nginx/sites-available/django.conf

server {
    listen 80;
    server_name xx.xxx.xxx.xx;

    location = /favicon.ico { access_log off; log_not_found off; }

    location / {
        include proxy_params;
        proxy_pass http://unix:/home/ubuntu/harrowgolf_dj/harrowgolf/app.sock;
    }

    location /static/ {
        root /home/ubuntu/harrowgolf_dj/harrowgolf;
    }

    location /media/ {
        root /home/ubuntu/harrowgolf_dj/harrowgolf;
    }

}

##### Step 26: เช็ค syntax ของไฟล์ sites-available/django.conf
sudo nginx -t

##### Step 27: สร้าง symbolic link ของไฟล์ sites-available/django.conf ไปยัง sites-enabled
sudo ln -s /etc/nginx/sites-available/django.conf /etc/nginx/sites-enabled

##### Step 28: restart nginx
sudo service nginx restart

##### Step 29: ตรวจสอบ status ของ nginx
sudo service nginx status

- หากพบปัญหาใชัคำสั่ง restart gunicorn
cd /etc/supervisor/conf.d
sudo supervisorctl restart all

##### Step 30: ทดสอบเข้าไปยัง ip address ของ EC2 instance ด้วย web browser
http://xx.xxx.xxx.xx/

##### Step 31: migrate database
cd /home/ubuntu/harrowgolf_dj/harrowgolf
python manage.py migrate

##### Step 32: สร้าง superuser
python manage.py createsuperuser

sample
username: admin
email address: admin@email.com
password: 123456

##### Step 33: สร้างไฟล์ static
cd /home/ubuntu/harrowgolf_dj/harrowgolf
python3 manage.py collectstatic

##### Step 34: ทดสอบเข้าใช้งาน admin site
http://xx.xxx.xxx.xx/admin


##### Trip & Trick
- การ Allow remote connection ของ MySQL บน EC2 instance
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

- แก้ไขไฟล์ mysqld.cnf ดังนี้
bind-address = 0.0.0.0

- รีสตาร์ท mysql
sudo service mysql restart

- Login to mysql
mysql -u root -p

- เรียกดู user ทั้งหมด
SELECT user, host, plugin FROM mysql.user;

- เปลี่ยน user ที่มี host คือ localhost เป็น %
UPDATE mysql.user SET host='%' WHERE user='samit';

- สร้าง user สำหรับ remote connection
CREATE USER 'sirirat'@'%' IDENTIFIED WITH mysql_native_password BY 'xxx';

- Grant all privileges
GRANT ALL PRIVILEGES ON *.* TO 'sirirat'@'%' WITH GRANT OPTION;

- Flush privileges
FLUSH PRIVILEGES;

- ออกจาก mysql
exit

- add inbound rule ใน security group ของ EC2 instance
type: MYSQL/Aurora