### Starting your Django project

Step 1:

```
$ mkdir projects
$ cd projects
projects $ mkdir myhellowebapp
projects $ cd myhellowebapp
```

### Start/active your virtual environment

> source ~/envs/tutorial-env/bin/activate

You should see something like this in your command line before the folder
structure - the (venv) indicates you're in the virtual environment:

```
(tutorial-env) (base) Bhumins-MacBook:myhellowebapp bhuminbhandari$
```

### Start your Django project

We installed Django, now we can use Django to build all the starting files we
need for our web app. In your command line (again, in your project folder with
your environment activated):

```
$ django-admin.py startproject hellowebapp .
```

This is going to start a Django project in your currect directory.

- django-admin.py: The script we'll be running.
- startproject: The specific utility we're using.
- hellowebapp: The name we're giving the project.
- . : The location where we're starting the project, with `.` denoting the
  current directory.

`startproject` will create these files and folders:

```
myhellowebapp/
    manage.py
    hellowebapp/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

The myhellowebapp folder is your top level folder.

- `manage.py`: We won't edit this file, but will use this file in the command line
  to interact with your project. You'll see it in action soon.
- The inner `hellowebapp` folder holds your project.
- `__init__.py`: Ignorable - tells Python that this is a Python package.
- `settings.py`: Aptly named - contains your settings.
- `urls.py`: URL declarations for the project. Important and we'll go over this
  soon.
- `wsgi.py`: Not needed at this point until you deploy your project.

### Create a Django app

A project can run many apps (all doing something distinct), but we're just going
to focus on having one for now, which is all you'll need for a very long
time.

In your top level folder (the one with _manage.py_ in it), run this command:

```
$ django-admin.py startapp collection
```

Like before, `django-admin.py` is the script, `startapp` is the command, and
`collection` is the name we're giving the app, which you can change if you wish.

`startapp` will create an additional folder and a few files:

```
myhellowebapp/
    manage.py
    collection/
        __init__.py
        admin.py
        migrations/
        models.py
        tests.py
        views.py
    hellowebapp/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

Note the additional "collection" folder in your project.

- `__init__.py`: Ignorable.
- `admin.py`: Contains admin codebits.
- `models.py`: Where you'll define the dynamic data that'll go in your database.
- `tests.py`: Tests you'll create to run to test your app automatically.
- `views.py`: Where the logic goes that powers your website.

If that's a bit complicated, don't worry about it yet because we'll review it
all later when we specifically start working with all those files.

### Add your new app to your settings file

We need to tell the project that we've added an app to it. Open up your
`settings.py` file (which is under your `hellowebapp` folder, see the directory
tree above).

Find the `INSTALLED_APPS` and add the name of your app to the beginning of the list
(don't forget the trailing comma):

```python
INSTALLED_APPS = (
    'collection', # this is the app we added
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
)
```

## Set up your database

Django has some fancypants utilities built in to keep your database (where
all your dynamic information is stored) managable. We need to run the initial
migration before we start the app, so in your top level folder (the one with
_manage.py_ in it), type this in:

```
$ python manage.py migrate
```

It's going to create your database automatically for you and port over some
information. Don't worry about understanding this just yet - we'll go over
databases and migrations a bit more in the "Adding Dynamic Data" chapter of
Hello Web App.

## Start your Django web app

Want to see if everything worked? In your terminal, head over to your top level
myhellowebapp folder (make sure you're in the folder with _manage.py_) and run
this command:

```
$ python manage.py runserver
```

...and you'll see the local Django development server starting, which'll serve
your project to your computer.

```
Validating models...

0 errors found
March 26, 2014 - 15:50:53
Django version 1.7.8, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

Now just head to your favorite web browser and visit
[http://127.0.0.1:8000](http://127.0.0.1:8000), where you'll see a "Welcome to
Django" page. Congrats on starting Django!

### [install DOC](https://docs.djangoproject.com/en/3.1/topics/install/#installing-official-release)

### [pip install DOC](https://pip.pypa.io/en/stable/installing/#upgrading-pip)

### [Virtual ENV DOC](https://docs.python.org/3/tutorial/venv.html)
