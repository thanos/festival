#festival
[![Build Status](https://travis-ci.org/thanos/festival.svg?branch=master)](https://travis-ci.org/thanos/festival)

A django art, film, music or whatever festival. Check out the project's [documentation](http://thanos.github.io/festival/).

# Prerequisites
- [virtualenv](https://virtualenv.pypa.io/en/latest/)
- [postgresql](http://www.postgresql.org/)
- [redis](http://redis.io/)
- [travis cli](http://blog.travis-ci.com/2013-01-14-new-client/)
- [heroku toolbelt](https://toolbelt.heroku.com/)

# Initialize the project
Create and activate a virtualenv:

```bash
virtualenv env
source env/bin/activate
```
Install dependencies:

```bash
pip install -r requirements/local.txt
```
Create the database:

```bash
createdb festival
```
Initialize the git repository

```
git init
git remote add origin git@github.com:thanos/festival.git
```

Migrate the database and create a superuser:
```bash
python festival/manage.py migrate
python festival/manage.py createsuperuser
```

Run the development server:
```bash
python festival/manage.py runserver
```

# Create Servers
By default the included fabfile will setup three environments:

- dev -- The bleeding edge of development
- qa -- For quality assurance testing
- prod -- For the live application

Create these servers on Heroku with:

```bash
fab init
```

# Automated Deployment
Deployment is handled via Travis. When builds pass Travis will automatically deploy that branch to Heroku. Enable this with:
```bash
travis encrypt $(heroku auth:token) --add deploy.api_key
```
