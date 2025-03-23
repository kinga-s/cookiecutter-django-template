# Django cookiecutter template
## This is a Django project template managed with Poetry for dependency management.
* To see all poetry installed dependencies: pyproject.toml -> [tool.poetry.group.dev.dependencies]
* Project is using python-decouple for environment setup.
* Default database is PostgreSQL (PostgreSQL database works on Docker, check docker-compose.yml file)

# Getting Started

## 1. Install cookiecutter:
```shell
pip install cookiecutter
```

## 2. Create a new project using this template:
```bash
cookiecutter https://github.com/kinga-s/cookiecutter-django-template.git
```

## 3. Follow README.md in your project to set up the rest.