# react_django

```
python3 -V
Python 3.8.6
python3 -m venv venv_django
source venv_django/bin/activate
(venv_django) which python
/Users/takahashifuyuki/work/Git/react_django/venv_django/bin/python
(venv_django)
```

```
(venv_django) python -m pip list
Package    Version
---------- -------
pip        20.2.1
setuptools 49.2.1
WARNING: You are using pip version 20.2.1; however, version 21.1.2 is available.
You should consider upgrading via the '/Users/takahashifuyuki/work/Git/react_django/venv_django/bin/python -m pip install --upgrade pip' command.

(venv_django) python -m pip install --upgrade pip
Collecting pip
  Using cached pip-21.1.2-py3-none-any.whl (1.5 MB)
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 20.2.1
    Uninstalling pip-20.2.1:
      Successfully uninstalled pip-20.2.1
Successfully installed pip-21.1.2
(venv_django)
```

```
(venv_django) takahashifuyuki@MacMini-FT react_django % python -m pip install djangorestframework
Collecting djangorestframework
  Downloading djangorestframework-3.12.4-py3-none-any.whl (957 kB)
     |████████████████████████████████| 957 kB 4.7 MB/s
Collecting django>=2.2
  Downloading Django-3.2.3-py3-none-any.whl (7.9 MB)
     |████████████████████████████████| 7.9 MB 9.7 MB/s
Collecting pytz
  Downloading pytz-2021.1-py2.py3-none-any.whl (510 kB)
     |████████████████████████████████| 510 kB 56.4 MB/s
Collecting sqlparse>=0.2.2
  Using cached sqlparse-0.4.1-py3-none-any.whl (42 kB)
Collecting asgiref<4,>=3.3.2
  Downloading asgiref-3.3.4-py3-none-any.whl (22 kB)
Installing collected packages: sqlparse, pytz, asgiref, django, djangorestframework
Successfully installed asgiref-3.3.4 django-3.2.3 djangorestframework-3.12.4 pytz-2021.1 sqlparse-0.4.1
(venv_django) takahashifuyuki@MacMini-FT react_django % python -m pip list
Package             Version
------------------- -------
asgiref             3.3.4
Django              3.2.3
djangorestframework 3.12.4
pip                 21.1.2
pytz                2021.1
setuptools          49.2.1
sqlparse            0.4.1
(venv_django) takahashifuyuki@MacMini-FT react_django %
```

```
(venv_django) takahashifuyuki@MacMini-FT react_django % django-admin startproject music_controller
(venv_django) takahashifuyuki@MacMini-FT react_django % cd music_controller
(venv_django) takahashifuyuki@MacMini-FT music_controller % django-admin startapp api
```

music_controller/music_controller/settings.py

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'api.apps.ApiConfig',
    'rest_framework'
]
```

music_controller/api/urls.py

```
from django.urls import path
from .views import main

urlpatterns = [
    path('', main)
]


```

# アプリを初めて実行する場合、view・データベース更新された時にコマンド実行する

python ./manage.py makemigrations

```
(venv_django) takahashifuyuki@MacMini-FT music_controller % python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
(venv_django) takahashifuyuki@MacMini-FT music_controller %
```

frontend

```
(venv_django) takahashifuyuki@MacMini-FT music_controller % django-admin startapp frontend
(venv_django) takahashifuyuki@MacMini-FT music_controller % cd frontend
(venv_django) takahashifuyuki@MacMini-FT frontend % npm init -y
Wrote to /Users/takahashifuyuki/work/Git/react_django/music_controller/frontend/package.json:

{
  "name": "frontend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}


npm notice
npm notice New minor version of npm available! 7.3.0 -> 7.15.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v7.15.0
npm notice Run npm install -g npm@7.15.0 to update!
npm notice
(venv_django) takahashifuyuki@MacMini-FT frontend % npm i webpack webpack-cli --save-dev

added 121 packages, and audited 122 packages in 8s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
(venv_django) takahashifuyuki@MacMini-FT frontend % npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev

added 160 packages, and audited 282 packages in 9s

24 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

(venv_django) takahashifuyuki@MacMini-FT frontend % npm i react react-dom

added 5 packages, and audited 287 packages in 3s

24 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
(venv_django) takahashifuyuki@MacMini-FT frontend %
(venv_django) takahashifuyuki@MacMini-FT frontend % npm install @material-ui/core

added 37 packages, and audited 324 packages in 5s

28 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

(venv_django) takahashifuyuki@MacMini-FT frontend % npm install @babel/plugin-proposal-class-properties

up to date, audited 324 packages in 1s

28 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
(venv_django) takahashifuyuki@MacMini-FT frontend % npm install react-router-dom

added 10 packages, and audited 334 packages in 2s

28 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
(venv_django) takahashifuyuki@MacMini-FT frontend % npm instal @material-ui/icons

added 1 package, and audited 335 packages in 5s

28 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

```
