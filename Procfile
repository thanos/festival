web: newrelic-admin run-program gunicorn --pythonpath="$PWD/festival" wsgi:application
worker: python festival/manage.py rqworker default