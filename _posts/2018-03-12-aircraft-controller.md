---
layout: post
title: Aircraft controller
date: 2018-03-12 12:08 +1300
---

What have I done? 

The text area on the Aircraft.php had a problem pushing data through and the reason for this was, the variables in the prepared statement where they bind to the insert query were incorrect. Text areas are now pushing to the comments table in the database.

Testing the aircraft controller pushing all fields to the database without any errors.

![alt text](/assets/testing.PNG "Aircraft Testing ")

Fig 1. Aircraft Controller pushing to the database – used a var_dump to show the above output

![alt text](/assets/testing1.PNG " Aircraft Testing db ")

Fig 2. Phpmyadmin showing data in the database – above is the person's table

What are my obstacles? 

The pilot’s medical section on the form seems to require a new table. We will need to create a new table in the database and will need to discuss where to join the table. 

Solution to above is, found the fields in the pilot table. Note to self-do some reading and searching before talking to the team about making changes.

Want to achieve? 

Start working on the new controller and get it working before the week's deadline.
