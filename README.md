# ChatterBot

This is an example Django app that shows how to create a simple chat bot web
app using [Django](https://ww.djangoproject.com) and [ChatterBot](https://github.com/gunthercox/ChatterBot).

## Documentation

Start the Django app by running 

``` Bash
python manage.py runserver 0.0.0.0:8000
```

If you running first time create chatterbot table before starting server

``` Bash
python manage.py migrate --run-syncdb
```

Further documentation on getting set up with Django and ChatterBot can be found in the [ChatterBot documentation](http://chatterbiot.readthedocs.io/en/latest/django.html)

## Make migrations

``` Bash
python manage.py migrate
```
## Train your bot

``` Bash
python manage.py train
```

## Training Corpus Path
The chatterbot [corpus path](https://github.com/gunthercox/chatterbot-corpus/tree/master/chatterbot_corpus/data/english) can be found here.

## Bot Django Settings
You could found Bot settings [here](./example_app/settings.py)

``` Python
CHATTERBOT = {
    'name': 'Heroku ChatterBot Example',
    'logic_adapters' : [
        "chatterbot.logic.BestMatch"
    ],
    'trainer': 'chatterbot.trainers.ChatterBotCorpusTrainer',
    'training_data': [
        'chatterbot.corpus'
    ]
}
```

If your app din't responding try to shift to postgresql, you will need install the ``dj_database_url`` package, to work nicely with PostgreSQL DB on heroku.

And also you will modify your settings.py as follows:

``` Python
import dj_database_url
DATABASES={'default': dj_database_url.config()}
```

### Allowed Hosts
Include your address at the ALLOWED_HOSTS directives in settings.py - Just the domain, make sure that you will take the protocol and slashes from the string

for example
``` Python
ALLOWED_HOSTS = ['127.0.0.1', 'chatterbot-live-example.herokuapp.com']
```
