# Authentification Using Google OAuth2 and JWT

<p>
<a href="https://github.com/psf/black"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-000000.svg"></a>

<img alt="npm" src="https://img.shields.io/npm/v/npm?color=brightgreen">
<a href="https://www.python.org/downloads/release/python-396/"><img alt="Python version" src="https://img.shields.io/badge/python-3.9.6-brightgreen.svg"></a>
<img alt="node-current" src="https://img.shields.io/node/v/npm">

<img alt="Github last-commit" src="https://img.shields.io/github/last-commit/ana-gujabidze/Google-Oauth2">
<img alt="GitHub code size in bytes" src="https://img.shields.io/github/languages/code-size/ana-gujabidze/Google-OAuth2">
</p>

---
The web application allows to sign in using Google OAuth2 and later on use locally generated JSON Web Token(JWT) to communicate between front-end and back-end.

On the back-end JWT authorization endpoints offer two token types — a short-living Access Token and a long-living Refresh Token.

---

## Common Usage

Django + React web application allows to:

- login to web application using Google OAuth2

- have access to protected area only after being loged in

- without authentification to have access only to landing page, which has only Google login button

- view user email in navigation dropdown name after authentification, before that dropdown name is populated with Anonymous

- refresh JWT without logging user out

---

## Prerequsites

- Python

- Python Virtual Environment (preferable)

- Git

- Docker

- Node

---

## Common setup

Clone the repo and install the dependencies.

```bash
git clone https://github.com/ana-gujabidze/Google-Oauth2.git
cd Google-Oauth2/
```

Download Docker Desktop from [the official website](https://docs.docker.com/desktop/). It will automatically install docker compose for you.

Create `.env` file similar to `.env_sample` file and specify all environmental variables both for client and server sides.

---

### Run application locally

If virtual environment is available run the following command

```python
pip3 install -r server/requirements.txt
```

In order to run server successfully, first production build should be created and imported into root directory of the back-end project.

```bash
npm run build
mv build/ ../server/
```

From here server can be started successfully.

First make migrations and then start the server:

```python
python3 manage.py makemigrations

python3 manage.py migrate

python3 manage.py runserver
```

Open [http://127.0.0.1:8000](http://127.0.0.1:8000) in the browser and result should be the following :

![login_page](__screenshots/login_page.png?raw=true "Title")

---

### Build Images and Run Containers With Docker Client

Navigate to the source directory and from there run command in order to build the image

```bash
docker build -t django-auth-app .
```

After successful build, run the container by the command

```bash
docker run -it -p 8000:8000 --env-file .env django-auth-app
```

After running Django app image, in CLI server URL should appear, after following it, the result should be the following:

![login_page](__screenshots/login_page.png?raw=true "Title")

---

## Testing

Run tests in the command line by following command

```python
cd server

pytest
```

In the command line following result should be present:

![executed_test_cases](__screenshots/test_result.png?raw=true "Title")
