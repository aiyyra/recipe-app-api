# recipe-app-api

Recipe API project Udemy

create repo in git
add secret (user n password) from docker

requirements.txt
contains library version that is required for our project
may update to newer version later

Dockerfile
contain dependencies for our project
create image(kind off object) and the version
maintainer
unbuffuer
requirement
directory and ports
run function and user

docker-compose.yml
use docker compose services to run our app
config the use of docker-compose syntax in the file

Linting and Testing
Linting :-
for : check code formats error dll
use by : install flake8, run from docker compose
syntax: docker-compose run --rm app sh -c "flake8"
Testing :-
use : Django test suite
syntax: docker-compose run --rm app s -c "python manage.py test"

Create requirement.dev.txt for linting n testing
reason : seperate the test and actual requirement from docker image
update docker compose to only allow dev requirement when in dev mode

add .flake8 file in app and list the excluded file (file we not going to linting)

Create Django app with docer compose
Syntax: docker-compose run --rm app sh -c "django-admin startproject app ."

Running the dev server on port 8000(127.0.0.1:8000)
(start)Syntax: docker-compose up
(stop): ctrl+c

Github Actions
-automation tool
-common uses = deploymwnt/linting/unit test
1 setup trigger (we use pushing code as trigger)
2 job (run the unit test)
3 result (success/fail)
pricing = charged per minutes
we have 2000 free minutes

configuring github actions
-create config file (.github/workflows/checks.yml) and set trigger
-config dockerhub auth (including add secret (Docker auth) to github)
-set .github n workflows folder for checks.yml file

Django test framework
-from unittest library
-can make tests.py or tests directory to stored the test modules
-Use TDD to create test file, simple example is on calc.py and test.py for calc module

Mocking
-override n change dependencies when testing
-use unittest.mock library

- testing the code functionality without it actually running it fully

Config Database (PostGreSQL)

> Add Database to docker-compose.yml
> -config Django
> -install database adaptor (psyopsg2)
> -update environment to include adapter
> add database and adapter to settings.py

fixing database race condition(so the db and app can run together withour any problem)
create the core folder and remove unnecessary files + add core to apps settings
-add commands and test commands
-create wait for db command to wait for database to be available to resolve the issue
-create the test and finish the actual command

Database migration (to use our database)
-Django ORM (Object Relational Mapper) handles db syntax
Start by defining models
use django to generate migration files
setup database
store data with interaction with model
a models contain name, fields, metadata, custom python login

to create migration
-define models
-s=ensure app is enable in settings.py
-create migration files, use django CLI: python manage.py makemigrations
-apply migration to db, use django CLI: python manage.py migrate

/update docker-compose.yml file so the commands wait for db b4 the sercer start
/update ci/cd to do the same
