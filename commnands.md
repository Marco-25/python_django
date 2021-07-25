## Comandos

- instalar pyenv
    -  sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm gettext libncurses5-dev tk-dev tcl-dev blt-dev libgdbm-dev git python-dev python3-dev aria2

    - curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash

    - pyenv install -l ou qual versao quer instalar
    - pyenv versions
    - setar versao do python
        - pyenv global version1 version2 version


    - criar ambiente virtual
        - pipenv install
        - iniciar ambiente virtual
          - pipenv shell

    - instalar django
        - pipenv install django

    - instalar mypy flake8
      - pipenv install --dev mypy flake8

    - iniciar projeto django
      - django-admin startproject name_project .

    - ajuda
      - python manager.py --help

    - criar alias
      - echo $VIRTUAL_ENV
      - alias mg='python $VIRTUAL_ENV/../manage.py'

    - criar arquivo Procfile
        - conteudo do arquivo: web: gunicorn name_project.wsgi --log-file -

    - instalar gunicorn
        - pipenv install gunicorn

    - iniciar aplicação no heroku pela linha de comando (foi instalda a cli do heroku, sem ela nn da)
        - heroku apps:create name_application

    - fazer deploy
        - git push heroku main:master -f
        - vai acontecer um erro, resolva assim
            - heroku config:set DISABLE_COLLECTSTATIC=1 (obs: colar no terminal e da enter)

    - criar app
        - mg startapp ( cria uma estrutura basica)

    - instalar pytest-django
        - pipenv install 'pytest-django'
        - criar arquivo [pytest.ini] colocar conteudo: obs duvidas ver documentação
        -   # -- FILE: pytest.ini (or tox.ini)
            [pytest]
            DJANGO_SETTINGS_MODULE = test_settings
            # -- recommended but optional:
            python_files = tests.py test_*.py *_tests.py

    - instalar pytest-cov
        - pipenv install --dev 'pytest-cov' -> pytest --cov=django_pro

    - instalar django-stubs
        - pipenv install --dev django-stubs : conteudo
        [mypy]
        plugins =
            mypy_django_plugin.main

        strict_optional = True

        [mypy.plugins.django-stubs]
        django_settings_module = demo.settings

    - instalar python-decouple
        - pipenv install 'python-decouple'

    - mudar debug para false no heroku
        - heroku config:set DEBUG=False
        - mostar varias de ambiente no heroku
             - heroku config

    - gerar chave secret_key aleatoria
        - abra o terminal rode:
            - from django.core.management.utils import get_random_secret_key
        - setar variavel ambiente secret_key no heroku
            -heroku config:set SECRET_KEY='valor gerado pela funcao get_random_secret_key'

    - adicionar dominio
        - heroku domais:add name_of_domnain (vai retornar um cname(dns))

    - configurar variavel amniente hosts
        - heroku config:set ALLOWED_HOSTS=project-django-training.herokuapp.com

    - instalar dj-database-url
        - pipenv install dj-database-url

    - instalar psycopg2-binary (conector do postgres)
        - pipenv install psycopg2-binary

    - coletar arquivos estaticos
        - mg collectstatic

    - apos configurar a AWS instalar a biblioteca django-s3-folder-storage
        - pipenv install django-s3-folder-storage
        - configurar e apos rodar: mg collectstatic --no-input

    - backup do postgres
        - heroku pg:backups:schedule DATABASE_URL --at '02:00 America/Sao_Paulo'
        - conferir backups
            - heroku pg:backups:schedules
            - baixar backup
                - heroku pg:backups:download
                - conferir backups
                    - heroku pg:backups

    - instalar django-debug-toolbar
        - pipenv install django-debug-toolbar

    - criar usuario na heroku
        - heroku run python manage.py createsuperuser