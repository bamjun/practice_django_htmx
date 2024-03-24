[깃링크](https://github.com/andyjud/django-starter-assets)  
[유튜브](https://www.youtube.com/watch?v=SQ4A7Q6_md8)  

OS : windows11  
Terminal : bash shell  


---  

# 1. 초기세팅    

- 가상환경 만들기  
  
  &darr; `/` &darr; `bash shell`
  ```bash  
  python -m venv .venv  
  ```  

<br>  

- 가상환경 진입 파일만들기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  echo ". '.venv/Scripts/activate'" > v
  ```  

  <br>

- 위 명령어 실행 후 ". v" 명령어로 가상환경 진입.  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  . v
  ```  

  <br>

- 패키지 설치를 위한 requirements.txt 만들기  

  &darr; `/` &darr; `bash shell`
  ```bash
  touch requirements.txt
  ```

  <br>

- 설치할 패키지 requirements.txt 에 입력하기  

  &darr; `/` &darr; `requirements.txt`
  ```txt
  Django
  pillow
  django-cleanup
  django-allauth
  django-htmx
  ```

  <br>
  
- 가상환경에 패키지 설치하기  

  &darr; `/` &darr; `bash shell`
  ```bash
  pip install -r requirements.txt
  ```

  <br>

- pip 업그레이드 하기  

  &darr; `/` &darr; `bash shell`
  ```bash
  pip install --upgrade pip
  ```

  <br>

---  

# 2. 장고 설정  

- 장고 설치하기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  django-admin startproject a_core .
  ```

  <br>

- 데이터 베이스 셋업하기    
  
  &darr; `/` &darr; `bash shell`
  ```bash
  python manage.py migrate
  ```
  ![alt text](images/markdown-image.png)

  <br>

- 장고 서버 정상작동 확인하기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  python manage.py runserver
  ```
  ![alt text](images/markdown-image-1.png)  
  ![alt text](images/markdown-image-2.png)  

  <br>

- 장고앱 'a_home' 설치하기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  python manage.py startapp a_home
  ```

  <br>
 
- `a_home`를 INSTALLED_APPS에 추가하기  
  
  &darr; `a_core/` &darr; `settings.py`
  ```python
  INSTALLED_APPS = [
      ...
      'a_home',
  ]
  ```
  ```diff
  """
  Django settings for a_core project.

  Generated by 'django-admin startproject' using Django 5.0.3.

  For more information on this file, see
  https://docs.djangoproject.com/en/5.0/topics/settings/

  For the full list of settings and their values, see
  https://docs.djangoproject.com/en/5.0/ref/settings/
  """

  from pathlib import Path

  # Build paths inside the project like this: BASE_DIR / 'subdir'.
  BASE_DIR = Path(__file__).resolve().parent.parent


  # Quick-start development settings - unsuitable for production
  # See https://docs.djangoproject.com/en/5.0/howto/deployment/checklist/

  # SECURITY WARNING: keep the secret key used in production secret!
  SECRET_KEY = 'django-insecure-915ypag@#aq+o%&b9sq!00mzmp&s31mo3u#e#v#6e)p*%hu3eq'

  # SECURITY WARNING: don't run with debug turned on in production!
  DEBUG = True

  ALLOWED_HOSTS = []


  # Application definition

  INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
  +   'a_home',
  ]

  MIDDLEWARE = [
      'django.middleware.security.SecurityMiddleware',
      'django.contrib.sessions.middleware.SessionMiddleware',
      'django.middleware.common.CommonMiddleware',
      'django.middleware.csrf.CsrfViewMiddleware',
      'django.contrib.auth.middleware.AuthenticationMiddleware',
      'django.contrib.messages.middleware.MessageMiddleware',
      'django.middleware.clickjacking.XFrameOptionsMiddleware',
  ]

  ROOT_URLCONF = 'a_core.urls'

  TEMPLATES = [
      {
          'BACKEND': 'django.template.backends.django.DjangoTemplates',
          'DIRS': [],
          'APP_DIRS': True,
          'OPTIONS': {
              'context_processors': [
                  'django.template.context_processors.debug',
                  'django.template.context_processors.request',
                  'django.contrib.auth.context_processors.auth',
                  'django.contrib.messages.context_processors.messages',
              ],
          },
      },
  ]

  WSGI_APPLICATION = 'a_core.wsgi.application'


  # Database
  # https://docs.djangoproject.com/en/5.0/ref/settings/#databases

  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.sqlite3',
          'NAME': BASE_DIR / 'db.sqlite3',
      }
  }


  # Password validation
  # https://docs.djangoproject.com/en/5.0/ref/settings/#auth-password-validators

  AUTH_PASSWORD_VALIDATORS = [
      {
          'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
      },
      {
          'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
      },
      {
          'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
      },
      {
          'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
      },
  ]


  # Internationalization
  # https://docs.djangoproject.com/en/5.0/topics/i18n/

  LANGUAGE_CODE = 'en-us'

  TIME_ZONE = 'UTC'

  USE_I18N = True

  USE_TZ = True


  # Static files (CSS, JavaScript, Images)
  # https://docs.djangoproject.com/en/5.0/howto/static-files/

  STATIC_URL = 'static/'

  # Default primary key field type
  # https://docs.djangoproject.com/en/5.0/ref/settings/#default-auto-field

  DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

  ```


  <br>

---  

# 3. 페이지 랜더링하기  
 
- home_view 함수 추가하기  
  
  &darr; `a_home/` &darr; `views.py`
  ```python
  def home_view(request):
    return render(request, 'home.html')
  ```
  ```diff
    from django.shortcuts import render

    # Create your views here.

  + def home_view(request):
  +   return render(request, 'home.html')
  ```

  <br>
 
- path 추가 하기.  
  
  &darr; `a_core/` &darr; `urls.py`
  ```python
  from a_home.views import *
  urlpatterns = [
      ...
      path('', home_view, name='home'),
  ]
  ```
  ```diff
    from django.contrib import admin
    from django.urls import path
  + from a_home.views import *

    urlpatterns = [
        path('admin/', admin.site.urls),
  +     path('', home_view, name='home'),
    ]
  ```


  <br>
 
- `templates` 만들기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  mkdir templates
  ```

  <br>
 
- templates 경로 지정해주기  
  
  &darr; `a_core/` &darr; `settings.py`
  ```python
  TEMPLATES = [
    {
        ...
        'DIRS': [ BASE_DIR / 'templates' ],
        ...
    },
  ]
  ```
  ```diff
    """
    Django settings for a_core project.

    Generated by 'django-admin startproject' using Django 5.0.3.

    For more information on this file, see
    https://docs.djangoproject.com/en/5.0/topics/settings/

    For the full list of settings and their values, see
    https://docs.djangoproject.com/en/5.0/ref/settings/
    """

    from pathlib import Path

    # Build paths inside the project like this: BASE_DIR / 'subdir'.
    BASE_DIR = Path(__file__).resolve().parent.parent


    # Quick-start development settings - unsuitable for production
    # See https://docs.djangoproject.com/en/5.0/howto/deployment/checklist/

    # SECURITY WARNING: keep the secret key used in production secret!
    SECRET_KEY = 'django-insecure-915ypag@#aq+o%&b9sq!00mzmp&s31mo3u#e#v#6e)p*%hu3eq'

    # SECURITY WARNING: don't run with debug turned on in production!
    DEBUG = True

    ALLOWED_HOSTS = []


    # Application definition

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'a_core',
    ]

    MIDDLEWARE = [
        'django.middleware.security.SecurityMiddleware',
        'django.contrib.sessions.middleware.SessionMiddleware',
        'django.middleware.common.CommonMiddleware',
        'django.middleware.csrf.CsrfViewMiddleware',
        'django.contrib.auth.middleware.AuthenticationMiddleware',
        'django.contrib.messages.middleware.MessageMiddleware',
        'django.middleware.clickjacking.XFrameOptionsMiddleware',
    ]

    ROOT_URLCONF = 'a_core.urls'

    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
  +         'DIRS': [ BASE_DIR / 'templates' ],
            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    'django.template.context_processors.debug',
                    'django.template.context_processors.request',
                    'django.contrib.auth.context_processors.auth',
                    'django.contrib.messages.context_processors.messages',
                ],
            },
        },
    ]

    WSGI_APPLICATION = 'a_core.wsgi.application'


    # Database
    # https://docs.djangoproject.com/en/5.0/ref/settings/#databases

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }


    # Password validation
    # https://docs.djangoproject.com/en/5.0/ref/settings/#auth-password-validators

    AUTH_PASSWORD_VALIDATORS = [
        {
            'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
        },
    ]


    # Internationalization
    # https://docs.djangoproject.com/en/5.0/topics/i18n/

    LANGUAGE_CODE = 'en-us'

    TIME_ZONE = 'UTC'

    USE_I18N = True

    USE_TZ = True


    # Static files (CSS, JavaScript, Images)
    # https://docs.djangoproject.com/en/5.0/howto/static-files/

    STATIC_URL = 'static/'

    # Default primary key field type
    # https://docs.djangoproject.com/en/5.0/ref/settings/#default-auto-field

    DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'


  ```

  <br>
 
- `base.html` 파일 생성하기  
  
  &darr; `/` &darr; `bash shell`
  ```bash
  touch templates/base.html
  ```

  <br>
 
- `base.html` 내용 작성하기  
  
  &darr; `templates/` &darr; `base.html`
  ```html
  {% load static %}
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Project Title</title>
      <link rel="icon" type="image/x-icon" href="{% static 'favicon.ico' %}">
      <script src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js" defer></script>
      <script src="https://unpkg.com/htmx.org/dist/htmx.js" defer></script>
      <script src="https://cdn.tailwindcss.com"></script>
      <style type="text/tailwindcss">
          [x-cloak] { 
              display: none !important; 
          }
          h1 {
              @apply text-4xl font-bold mb-4
          }
          h2 {
              @apply text-xl font-bold mb-2
          }
          p {
              @apply mb-4
          }
          .button, button, [type='submit'], [type='button'] {
              @apply bg-indigo-600 text-white font-bold px-6 py-4 inline-block 
              rounded-lg shadow-lg transition-all cursor-pointer
          }
          .button:hover, button:hover, [type='submit']:hover, [type='button']:hover {
              @apply bg-indigo-700
          }
          .button:active, button:active, [type='submit']:active, [type='button']:active {
              @apply scale-95
          }
          .button.alert, button.alert {
              @apply bg-red-700
          }
          .button.alert:hover, button.alert:hover {
              @apply bg-red-600
          }
          .button-red {
              @apply !bg-red-500 hover:!bg-red-600
          }
          .button-gray {
              @apply !bg-gray-300 hover:!bg-[#c3c9d0]
          }
          .navitems>li>a {
              @apply flex items-center gap-2 h-12 px-4 hover:bg-gray-700 rounded-lg;
          }
          .hoverlist>* {
              @apply hover:bg-gray-100 rounded-md transition duration-150;
          }
          .hoverlist>*>a {
              @apply flex items-center p-2;
          }
          .highlight {
              @apply !bg-indigo-100;
          }
          .allauth content a {
              @apply underline underline-offset-2
          }
          .allauth content a:hover {
              @apply text-indigo-500
          }
          .allauth form[action="/accounts/signup/"] ul {
              @apply hidden
          }
          .allauth form[action="/accounts/signup/"] ul.errorlist {
              @apply block
          }
          .allauth .helptext {
              @apply block mt-4
          }
          label {
              @apply hidden
          }
          input[type=file] {
              @apply bg-white pl-0
          }
          .textarea, textarea, input {
              @apply w-full rounded-lg py-4 px-5 bg-gray-100
          }
          .errorlist li {
              @apply p-1 pl-4 border-l-red-500 border-l-4 border-solid mb-2 text-red-500
          }
          label[for="id_remember"] {
              @apply inline-block w-auto mr-2
          }
          input[name="remember"] {
              @apply w-auto
          }
          .alert-info { @apply bg-blue-300 }
          .alert-success { @apply bg-green-400 }
          .alert-warning { @apply bg-amber-400 }
          .alert-danger { @apply bg-amber-500 }
      </style>
  </head>
  <body class="{% block class %}{% endblock %}">
  	
      <messages>
          {% if messages %}
          <div x-data="{ showMessage: false }" >
          {% for message in messages %}
          <div class="absolute left-0 right-0 max-w-xl mx-auto mt-3 px-4 z-50 ">
              <div x-cloak class="alert-{{ message.tags }} flex items-center py-3 pl-6 pr-4 bg-blue-500 text-white rounded-lg" role="alert"
              x-show="showMessage" 
              x-init="setTimeout(() => showMessage = true, 200), setTimeout(() => showMessage = false, 6000)"
              x-transition:enter="duration-700 ease-out"
              x-transition:enter-start="opacity-0 -translate-y-5"
              x-transition:enter-end="opacity-100 translate-y-0"
              x-transition:leave="duration-200 ease-in"
              x-transition:leave-start="opacity-100 translate-y-0"
              x-transition:leave-end="opacity-0 -translate-y-5">
                  <div>
                      <div class="text-lg">{{ message }}</div>
                  </div>
                  <div class="ml-auto cursor-pointer" @click="showMessage = false">
                      <svg fill="white" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" viewBox="0 0 24 24" stroke="currentColor" class="w-8 h-8 ml-2">
                          <path d="M6 18L18 6M6 6l12 12"></path>
                      </svg>
                  </div>
              </div> 
          </div>
          {% endfor %}
          </div>
          {% endif %}
      </messages>

      <header class="flex items-center justify-between bg-gray-800 h-20 px-8 text-white sticky top-0 z-40">
          <div>
              <a class="flex items-center gap-2" href="/">
                  <img class="h-6" src="/static/images/logo.svg" alt="Logo"/>
                  <span class="text-lg font-bold">Project Title</span>
              </a>
          </div>
          <nav class="block bg-gray-800 relative">
              <ul class="navitems flex items-center justify-center h-full">
                  {% if request.user.is_authenticated %}
                  <li><a href="/">Home</a></li>
                  <li x-data="{ dropdownOpen: false }" class="relative">
                      <a @click="dropdownOpen = !dropdownOpen" @click.away="dropdownOpen = false" class="cursor-pointer select-none">
                          <img class="h-8 w-8 rounded-full object-cover" src=""/>
                          Username
                          <img x-bind:class="dropdownOpen && 'rotate-180 duration-300'" class="w-4" src="https://img.icons8.com/small/32/777777/expand-arrow.png"/>
                      </a>
                      <div x-show="dropdownOpen" x-cloak class="absolute right-0 bg-white text-black shadow rounded-lg w-40 p-2 z-20"
                      x-transition:enter="duration-300 ease-out"
                      x-transition:enter-start="opacity-0 -translate-y-5 scale-90"
                      x-transition:enter-end="opacity-100 translate-y-0 scale-100"
                      >
                          <ul class="hoverlist [&>li>a]:justify-end">
                              <li><a href="">My Profile</a></li>
                              <li><a href="">Edit Profile</a></li>
  			    <li><a href="">Settings</a></li>
                              <li><a href="">Log Out</a></li>
                          </ul>
                      </div>
                  </li>
                  
                  {% else %}
  		<li><a href="">Login</a></li>
                  <li><a href="">Signup</a></li>
                  {% endif %}
              </ul>
          </nav>
      </header>

      <content class="block w-full">
          <div class="max-w-4xl mx-auto px-8 py-24">
              <h1>New Project</h1>
          </div>
      </content>

  </body>
  </html>
  ```

  <br>
 
- 
  
  &darr; `/` &darr; `bash shell`
  ```bash
  
  ```

  <br>
 
- 
  
  &darr; `/` &darr; `bash shell`
  ```bash
  
  ```

  <br>

- 
  
  &darr; `/` &darr; `bash shell`
  ```bash
  
  ```

  <br>
 
- 
  
  &darr; `/` &darr; `bash shell`
  ```bash
  
  ```

  <br>
 
<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

<br>  

--- 
---  
---  
# &darr; learned  

## 1. mkdir -p
`mkdir` 명령어는 유닉스 및 유닉스 계열 시스템에서 새 디렉토리(폴더)를 만드는 데 사용됩니다. 여기서 `-p` 옵션은 "parents"의 약자로, 지정된 디렉토리와 필요한 모든 상위 디렉토리를 함께 생성하는 역할을 합니다. 즉, 주어진 경로에 있는 중간 디렉토리가 없으면 `-p` 옵션을 사용하면 그 중간 디렉토리들도 모두 생성됩니다.

예를 들어, 다음 명령어를 실행한다고 가정해 봅시다:

```sh
mkdir -p /home/user/docs/newfolder
```

이 경우, `/home/user/docs` 경로가 아직 존재하지 않으면, `mkdir -p` 명령어는 `newfolder`와 함께 필요한 `/home`, `/home/user`, `/home/user/docs` 디렉토리를 모두 생성합니다. 이미 해당 경로가 존재하면 추가적인 에러 메시지 없이 무시하고 새로 지정된 디렉토리만을 생성합니다.

`-p` 옵션은 스크립트를 작성할 때 특히 유용하며, 디렉토리 구조를 프로그램적으로 생성할 때 필요한 디렉토리가 이미 있는지 확인할 필요 없이 바로 생성할 수 있게 해줍니다.

---