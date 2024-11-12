
# How to fix the error in python installation

first you need to Windows + R and type **regedit**.
![regefit image](https://github.com/Adornadowilliam2/python_error/blob/main/media/regedit.png?raw=true)

then find this LongPathEnabled and change 0 into 1 then restart then try again if it work 

![long path image](https://github.com/Adornadowilliam2/python_error/blob/main/media/longpathenabled.png?raw=true)

![change into one](https://github.com/Adornadowilliam2/python_error/blob/main/media/onetoadd.png?raw=true)


# Django Project Setup on Windows

This guide will walk you through the steps to create a Django app from scratch on a Windows machine. It covers setting up the environment, installing Django, creating a new project, and setting up an app.

## Prerequisites

- Python 3.x installed on your system.
- Basic knowledge of Python and web development.

## Step 1: Install Python and Set Up Virtual Environment

1. **Install Python**
   - Download the latest version of Python from the official [Python website](https://www.python.org/downloads/).
   - During installation, make sure to check the option **Add Python to PATH**.

2. Create a Virtual Environment Navigate to the directory where you want to create your Django project:

```php
mkdir django-crud
cd django-crud
python -m venv venv
venv\Scripts\activate
```
### To see it work you in the command prompt look like this

![image venv with](https://github.com/Adornadowilliam2/python_error/blob/main/media/venv%20before%20the%20dir.png?raw=true)

3. Install django

```php
pip install Django
```


4. Once it finish install you can check by typing this command: 

```php
django-admin --version
```

5. Then once it shows the version you can create your own project

```php
django-admin startproject mydjango-crud

```


you will see the structure look like this once it finish install


```php

mydjango-crud/
├── manage.py
└── mysite/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py

```

then type

```php
cd mysite

```
to run the server 

```php
python manage.py runserver
```

then go to your browser and type **http://localhost:8000** or click this to go the django default website









## Create an App in Django

just type

```php
python manage.py startapp myapp
```
this will the new structure look like separate to the django-crud earlier
```php
myapp/
├── admin.py
├── apps.py
├── __init__.py
├── models.py
├── tests.py
└── views.py
```

```php

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',  # Add your app here
]
```

you can myapp/views.py change it into

```php
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello, Django!")
```
then go back to mydjango-crud/urls.py

```php
from django.contrib import admin
from django.urls import path
from myapp import views  # Import views from your app

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home),  # Map the home view to the root URL
]
```
