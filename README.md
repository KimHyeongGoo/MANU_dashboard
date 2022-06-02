# Web-Django-Demo


## 실행법

> UNZIP the sources or clone the private repository. After getting the code, open a terminal and navigate to the working directory, with product source code.

```bash
$ # Get the code
$ git clone https://github.com/KimHyeongGoo/MANU_dashboard
$ cd MANU_dashboard
$
$ # Install modules - SQLite Storage
$ # install 오류 발생시 requirements.txt 파일에 있는 라이브러리 버전 지운 후 재시도
$ pip3 install -r requirements.txt
$
$ # Create tables
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Start the application (development mode)
$ python manage.py runserver # (default port 8000)
$
$ # Start the app - custom port
$ # python manage.py runserver 0.0.0.0:<your_port>
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```


## 파일 디렉토리 구조


```bash
< PROJECT ROOT >
   |
   |-- core/                               
   |    |-- settings.py                    # 외부 접근 허용 등 주요 설정 파일
   |    |-- wsgi.py                        
   |    ┕-- urls.py                        
   |
   |-- apps/
   |    |
   |    |-- home/                          
   |    |    ┕-- views.py                  # Serve HTML pages for authenticated users
   |    |    ┕-- urls.py                   # Define some super simple routes  
   |    |
   |    |-- authentication/                # Handles auth routes (login and register)
   |    |    ┕-- urls.py                   # Define authentication routes  
   |    |    ┕-- views.py                  # Handles login and registration  
   |    |    ┕-- forms.py                  # Define auth forms (login and register) 
   |    |
   |    |-- static/
   |    |    ┕-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component (사이드바 - 탭 메뉴)
   |         |    |-- sidebar.html         # Sidebar component (상단 바)
   |         |    |-- footer.html          # App Footer (하단 바)
   |         |    ┕-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                   # Master pages
   |         |    |-- base-fullscreen.html  # Used by Authentication pages
   |         |    ┕-- base.html             # Used by common pages
   |         |
   |         |-- accounts/                  # Authentication pages
   |         |    |-- login.html            # Login page
   |         |    ┕-- register.html         # Register page
   |         |
   |         ┕-- home/                      # UI (html) Pages
   |              |-- sw                    # 소프트웨어 기능 상세 페이지 디렉토리
   |              |-- dataset               # 데이터셋 상세 페이지 디렉토리
   |              |-- index.html            # Index page (메인페이지 - 대쉬보드)
   |              |-- sw.html               # 소프트웨어 기능 페이지
   |              |-- dataset.html          # 데이터셋 페이지
   |              |-- empirical_case.html   # 실증 사례 페이지
   |              ┕-- *.html                # All other pages
   |
   |-- requirements.txt                     # Development modules - SQLite storage
   |
   |-- .env                                 # Inject Configuration via Environment
   |-- manage.py                            # Start the app - Django default start script
   |
   |-- ************************************************************************
```

<br />

> The bootstrap flow

- Django bootstrapper `manage.py` uses `core/settings.py` as the main configuration file
- `core/settings.py` loads the app magic from `.env` file
- Redirect the guest users to Login page
- Unlock the pages served by *app* node for authenticated users

<br />

## Recompile CSS

To recompile SCSS files, follow this setup:

<br />

**Step #1** - Install tools

- [NodeJS](https://nodejs.org/en/) 12.x or higher
- [Gulp](https://gulpjs.com/) - globally 
    - `npm install -g gulp-cli`
- [Yarn](https://yarnpkg.com/) (optional) 

<br />

**Step #2** - Change the working directory to `assets` folder

```bash
$ cd apps/static/assets
```

<br />

**Step #3** - Install modules (this will create a classic `node_modules` directory)

```bash
$ npm install
// OR
$ yarn
```

<br />

**Step #4** - Edit & Recompile SCSS files 

```bash
$ gulp scss
```

The generated file is saved in `static/assets/css` directory.

<br /> 
