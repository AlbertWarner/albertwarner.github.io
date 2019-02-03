---
layout: post
title: 'Django Database Setup '
date: 2018-10-18 21:12 +1300
---

Creating the Database is interesting feature of Django, like flask you create the database in model.py file. Each Table is called a class in Django. For now, I will use Sqlite which comes standard with Django and I will implement the database into MariaDB at a later stage, just want to get everything working properly.

<h3> Creating a person table </h3>
```ruby
class Person(models.Model):
    FName = models.CharField(max_length = 128, null=True, blank=True)
    LName = models.CharField(max_length = 128, null=True, blank=True)
    Gender = models.IntegerField(null=True, default=0)
    DateofBirth = models.CharField(max_length = 64, null=True, blank=True)
    Email = models.CharField(max_length = 128, null=True, blank=True)
    def __str__(self):
        return self.FName
```

I used the exact same naming convention as what is being used in the phone app, when the API comes from the phone app, the data can be stored without any problems.

As I was creating the other tables, I noticed that not all the fields where Char fields and I used the <a href=" https://docs.djangoproject.com/en/dev/ref/models/fields/#floatfield"> Django Docs </a> to find the other fields such as the Boolean, the Float field and the Decimal Field.

Following the guidelines of <a href=https://docs.djangoproject.com/en/2.1/intro/tutorial02/>Django Docs tutorial</a>  to create the tables with Django you use the command “makemigrations wwl” but I ran into some problems along the way. 

<h3>First problem </h3>
```ruby
File "C:\Program Files (x86)\Python36-32\lib\site-packages\django\core\management\__init__.py", line 347, in execute
    django.setup()
  File "C:\Program Files (x86)\Python36-32\lib\site-packages\django\__init__.py", line 24, in setup
    apps.populate(settings.INSTALLED_APPS)
  File "C:\Program Files (x86)\Python36-32\lib\site-packages\django\apps\registry.py", line 112, in populate
    app_config.import_models()
  File "C:\Program Files (x86)\Python36-32\lib\site-packages\django\apps\config.py", line 198, in import_models
    self.models_module = import_module(models_module_name)
  File "C:\Program Files (x86)\Python36-32\lib\importlib\__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
  File "<frozen importlib._bootstrap>", line 994, in _gcd_import
  File "<frozen importlib._bootstrap>", line 971, in _find_and_load
  File "<frozen importlib._bootstrap>", line 955, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 665, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 678, in exec_module
  File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed
  File "H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite\wwl\models.py", line 5, in <module>
    class Person(models.Model):
  File "H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite\wwl\models.py", line 6, in Person
    FName = models.CharField(max_length = 128, null=true, blank=True)
NameError: name 'true' is not defined
PS H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite>  
```

What a huge list of complaints, only to find the null = true must be with a capital T. Wow Django is strict, seems to be shouting at you just because of an uppercase or lowercase letter. All good problem solved.  

The second problem was the Boolean field has null = true and on the error message it stated to make the field NullBooleanField but according to the Django Docs, this will be depreciated in new versions on Django.

<h3>Second problem </h3>
```ruby
wwl.Goal.Achieved: (fields.E110) BooleanFields do not accept null values.
        HINT: Use a NullBooleanField instead.
wwl.Goal.Active: (fields.E110) BooleanFields do not accept null values.
        HINT: Use a NullBooleanField instead.
PS H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite>  python -m django --version
2.0.2
PS H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite> python -V
Python 3.6.4
```

![alt text](/assets/images/Project2/image.png " Django Docs ")
Image 1. Django Docs on Null Boolean Field

The Solution to this problem is getting a newer version on Django, the version on the computer was 2.0.2 and the latest version where this problem won’t exist is version 2.1

After all that that Database was populated with tables, this was an awesome sight to see and fun working through those problems.

<h3>Successful creating DB Tables </h3>
```ruby
PS H:\BitY3\Semester 2\Project 2\walkingwithleon\Django-WWL\mysite> python manage.py makemigrations wwl
Migrations for 'wwl':
  wwl\migrations\0001_initial.py
    - Create model Geolocation
    - Create model Goal
    - Create model Person
    - Create model Session
    - Create model Weight
    - Add field PersonID to goal
    - Add field SessionID to geolocation
```

The last problem was on the admin page, this page is created by Django and it allows the user to view the DB in user-friendly view, you can add or remove information from the DB. Great way to test the DB.

According to Django docs, you must do the following: 

“It’s important to add __str__() methods to your models, not only for your own convenience when dealing with the interactive prompt, but also because objects’ representations are used throughout Django’s automatically-generated admin.”

I added this to the models.py file to all the tables, but I was getting an error because the field I was passing through was an INT and not a Char field. With a little help from Grayson, I changed the return function to string as shown in the code snippet below. Interesting, I wonder if I changed the __str__() to a __int__() would it accept it? Didn’t have time to test but will in the future.

<h3>String return function for DB </h3>
```ruby

def __str__(self):
        return str(self.personID) #user to select convert to string, this function returns a string
```

Interesting day today, had fun learning these new features and functions, different to PHP by far, but probably Laravel would have been the same.

<h3>Reflection</h3>
Learning how to create a database in Django and work through some problems with creating it. Django is strict. Instead of creating the DB with a query, Django does all that for you, very interesting.

