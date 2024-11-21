# Django-WebRtc
Django yordamida WebRtc bilan video va audio qo'ng'iroqlarni amalga oshirish

## Python3 yordamida Virtualenv yaratish
	virtualenv virtual/webrtc -p python3

## Django va barcha modullarni pip3 yordamida o'rnating
	pip3 install django
	django-admin startproject webrtc
	django-admin startproject webrtc .
	pip3 install Pillow
	pip3 install django-extensions
	pip3 install djangorestframework
	pip3 install django-rest-auth
	pip3 install django-cors-headers
	pip3 install django-filter
	pip3 install django-froala-editor
	pip3 install django-ckeditor
	pip3 install fcm_django
	pip3 install mysqlclient
	LDFLAGS=-L/usr/local/opt/openssl/lib pip install mysqlclient

## `requirements.txt` faylini yangilang
	pip3 freeze > requirements.txt

## Django loyihasini yaratish
	django-admin startproject webrtc

## Django ichida yangi ilova yarating
	python manage.py startapp home
	python manage.py startapp blog

## Django serverini ishga tushirish
	python manage.py runserver
	python manage.py runserver 8080
	python manage.py runserver 0:8000
	python manage.py runserver 192.168.1.4:8000

## Superuser yarating
	python manage.py createsuperuser

## Terminal orqali foydalanuvchi parolini tiklash
	python manage.py changepassword username

## Loyihani yoki ilovani migratsiya qilish
	python manage.py makemigrations
	python manage.py makemigrations blog

## Loyihani yoki ilovani migratsiya qilish
	python manage.py migrate
	python manage.py migrate blog
	python manage.py migrate --fake
	python manage.py migrate blog --fake

## Doimiy sozlamalar uchun bu buyruqni ishga tushiring
	export DJANGO_SETTINGS_MODULE=webrtc.settings.local

## Mahalliy tizimda ishlating
	DJANGO_SETTINGS_MODULE=webrtc.settings.local python manage.py runserver

## Test serverda ishlating
	DJANGO_SETTINGS_MODULE=webrtc.settings.testing python manage.py runserver

## Staging serverda ishlating
	DJANGO_SETTINGS_MODULE=webrtc.settings.staging python manage.py runserver

## CircleCI serverda ishlating
	DJANGO_SETTINGS_MODULE=webrtc.settings.circleci python manage.py runserver

## Ishlab chiqarish serverida ishlating
	DJANGO_SETTINGS_MODULE=webrtc.settings.production python manage.py runserver

## Statik fayllarni ishlab chiqarish serverida sozlash
	python manage.py collectstatic
	python manage.py collectstatic --noinput
	python manage.py collectstatic --noinput --clear

## Redis Channel Layer o‘rnating va sozlang
Redis xabarlarni jo'natish va qabul qilish uchun ishlatiladi. Avval Redis serverni Docker yoki tizimga to'g'ridan-to'g'ri o'rnating va ishga tushiring:
	
	Docker yordamida Redis serverni ishga tushirish:
	docker run -p 6379:6379 -d redis:2.8

Mac uchun Redis-ni o'rnating va ishga tushiring:
	brew install redis
	brew services start redis
	brew info redis

Ubuntu uchun Redis serverni o'rnating va ishga tushiring:
	sudo apt install redis-server
	sudo systemctl status redis
	sudo systemctl restart redis.service

Redis o'rnatilgandan so'ng:
	pip3 install channels_redis

## Django Channels-ni sozlash
	pip3 install -U channels
Loyihangiz katalogida `routing.py` faylini yarating va `ASGI_APPLICATION`ni `settings.py` faylga qo'shing.

---

# Heroku sozlamalari

## Heroku CLI-ni o'rnating
Heroku CLI-ni yuklab oling va o'rnating. Keyin Heroku hisobingizga kiring:
	$ heroku login

## Heroku loyihasini yarating
	heroku create webrtc

## Heroku buildpack sozlash
	heroku buildpacks:set heroku/python

## Git versiyasini tekshirish va reponi boshlash
	git --version
	git init

## Heroku sozlamalarini repo-ga qo‘shing
	heroku git:remote -a webrtc

## `Procfile` fayliga quyidagi kodni qo'shing
	web: gunicorn webrtc.wsgi

## Gunicorn va django-heroku o'rnating
	pip3 install gunicorn
	pip3 install django-heroku

## Sozlamalarda `django_heroku`ni import qiling
	import django_heroku
	django_heroku.settings(locals())

## Kodni Heroku-ga jo'nating va joylashtiring
	pip3 freeze > requirements.txt
	git status
	git add .
	git commit -m "Loyiha dastlabki sozlamalari"
	git push heroku master

## Statik fayllar bilan bog'liq xatolikni o'chirish
	heroku config:set DISABLE_COLLECTSTATIC=1

## Heroku bash orqali migratsiyalarni ishga tushirish
	heroku run bash
	python3 manage.py migrate
	python3 manage.py createsuperuser

## Xatolarni tekshirish uchun loglarni ko‘ring
	heroku logs --tail

---

### O'qiganingiz uchun rahmat! 😊
# Izzatbek Ulkanov! #
