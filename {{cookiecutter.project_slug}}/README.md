# Basic setup for Django applications (local development)
### This is a Django project template managed with Poetry for dependency management. 
* To see all poetry installed dependencies: pyproject.toml -> [tool.poetry.group.dev.dependencies]
* Project is using python-decouple for environment setup.
* Default database is PostgreSQL (PostgreSQL database works on Docker, check docker-compose.yml file)


## Prerequisites
Ensure you have the following installed:
* Python (>= 3.13.2, recommended: latest stable version)
* Git
* Docker (and Docker Compose if not bundled)

# Getting Started
### At this point you should have your app template project downloaded from github. Let's set up everything!

## 1. Create and activate a virtual environment

On macOS/Linux:
```shell
python -m venv .venv
source .venv/bin/activate
```

On Windows (Command Prompt):
```shell
python -m venv .venv
.venv\Scripts\activate
```

On Windows (PowerShell):
```shell
python -m venv .venv
.venv\Scripts\Activate.ps1
```
#### Configure Python 3.13 (your_app_name) as a project interpreter.

## 2. Install Poetry and dependencies
Install or upgrade pip to the latest version.
```shell
python -m pip install --upgrade pip
```
Install Poetry:
```shell
pip install poetry
```
Also check, if the venv that you previously created is the same venv poetry is using. You can check it by running:
```shell
poetry env info --path
```
(If you are inside Poetry venv, i.e. you don't need to type `poetry run` before a command.)

Install project dependencies:
```shell
poetry install
```

Initialize pre-commit in your repository:
```shell
pre-commit install
```

## 3. Django Project Environment Setup
Define environment variables in a .env file.

## 4. Start database
First, make sure you have Docker installed and started.
Run the following command to start the PostgreSQL container in detached mode:
```shell
docker-compose up -d
```
To check if the container is running, use:
```shell
docker ps
```

### Now you should be able to run:
```shell
python manage.py shell
```

You can also check if environment variables were set correctly by running the following commands in the shell:
```python
from decouple import config
print(config('DJANGO_SECRET_KEY'))  # Should output your secret key
print(config('DJANGO_DEBUG', cast=bool))  # Should output True or False
```

## 5. Apply Migrations
```shell
python manage.py migrate
```

## 6. Create a Superuser (Optional)
```shell
python manage.py createsuperuser
```

## 7. Run the Development Server
```shell
python manage.py runserver
```
Your Django application should now be running at http://127.0.0.1:8000/.

## Running Tests
To run tests, execute:
```shell
python manage.py test
```

## Linting & Formatting
To check code quality and format:
```
flake8 <folder_or_file_location>
black <folder_or_file_location>
```

## Deployment
For deployment, ensure you:
* Set DEBUG=False in .env.
* Configure allowed hosts and database settings.
* Use a WSGI server like Gunicorn for production.

## License
This project is licensed under the MIT License.