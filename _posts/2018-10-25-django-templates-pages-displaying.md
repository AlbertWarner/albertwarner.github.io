---
layout: post
title: 'Django templates pages displaying'
date: 2018-10-25 21:18 +1300
---

Back to walking with Leon, hello Django.

This would be a pretty simple day but just wanted to get a few things working before we hit the hard stuff. I have a template downloaded for the web app which I am using, and it look good, it had the right colours of purple, representing the same colours as the phone app.

I created the directory called static to store the CSS, JS and Img files and I created a templates directory to store the HTML files. 

In the head of the HTML, I change the path for CSS tags and used the Django method of loading the external files.

  <h3>Static Files Django </h3>
```django
{% raw %}
{% load staticfiles %}
  <link rel="apple-touch-icon" sizes="76x76" href="{% static 'img/apple-icon.png' %}">
  <link rel="icon" type="image/png" href="{% static 'img/favicon.png' %}">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <!-- CSS Files -->
  <link href="{% static 'css/black-dashboard.css' %}" rel="stylesheet" type="text/css"/>
  {% endraw %}
```

I changed the index methods in views.py file to call the HTML files in the template directory and It worked!! The pages were running through the Django server and now I have templates displaying. I got the dashboard and the user page to display, removed some unnecessary code from the create, like his GitHub pages etc.

<h3>Reflection</h3>
I learned that Django does not create the directory where to store files like CSS etc, they need to be created. Learned this while doing ACL that its best practice and Django use a directory called static. Also, I learn how to use the static pathing in Django instead using the full path to files.  
