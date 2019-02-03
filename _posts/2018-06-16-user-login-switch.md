---
layout: post
title: User Login Switch
date: 2018-06-16 01:26 +1200
---

Matt created the login in page, which worked awesomely, but I had to tweak it. I started off by adding JavaScript to echo if the user had entered the incorrect password or username.

![alt text](/assets/access.JPG " access ")

Fig1. Access Control

In fig 1, I used a switch on the username and when it hit the variable the header would include a certain controller. For example, if the admin logged in, it will call the indexcontroller.php   

It is fun to see the different users log in and different controllers being called from the access controller.


