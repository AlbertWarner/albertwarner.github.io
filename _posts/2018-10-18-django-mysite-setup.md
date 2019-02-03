---
layout: post
title: 'Django Mysite Setup  '
date: 2018-10-18 21:09 +1300
---

Django is a smart framework (MVC) and can be complex to get your head around, but it has a few tutorials and videos on what to do and some interesting learning tips. Django is very similar to Flask but as explained you have to do the Django way, or it won’t work, Flask has more freedom to develop the way you want.

I followed the <a href="https://docs.djangoproject.com/en/2.1/intro/tutorial01/">Django tutorial</a> and it was simple to start the application.

I created the mysite project and created another app called “wwl” abbreviated for walking with Leon but since then I have heard the name of the app has changed, not to sure what to do but I will carry on for now and get hopefully most of it completed and displaying some dummy data and the names can change closer to .  

Getting back to work the mysite is the main web app and well is the sub app.

The interesting part of the build will be the paths, going to be something fun to learn and get better at it and understand what is happening.

For now, please note we will be using localhost, which is a development server which Django creates and it hosts the website.

In the mysite/urls.py, we redirected the user when they hit the sites localhost address, the user will be directed to the wwl/urls.py which then will direct the user to a webpage.

<h3> Mysite – urls.py file paths </h3>
```ruby
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('wwl.urls')),
]
```
 
The urls.py file in WWL will call in index method created in the views.py file

<h3> WWL – urls.py file </h3>
```ruby
urlpatterns = [
    path('', views.index, name='index'),
```

For testing purpose, I created a method in the views.py file which displayed template with "Hello World" written on it.

<h3> View.py Hello World </h3>
```ruby
def index(request):
    return HttpResponse ("<h1>Hello World</h1>")
```

<h3>Reflection</h3>
Setting up Django is pretty easy with the commands. It takes almost 3 commands and website is setup and working for you, well the server that is. The file paths are going to be a interesting learn but I will get my head around it.
