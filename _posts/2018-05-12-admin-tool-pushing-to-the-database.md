---
layout: post
title: Admin Tool Pushing to the Database
date: 2018-05-12 23:39 +1200
---

The admin tool was the first page that had to be working because the database was clear of all data and our index page would not have anything to display. The index controller also uses the form Table in the DB to connect to the forms controllers. The entire website would not work without those important forms and form ID’s. 

We weren’t too focused on the main objective and that was to get data into the DB with the admin tool. Arron came to help me with his web skills and we worked on getting the admin tool displaying correctly, meaning the files were not seeing the CSS or the images in the assets directory.

![alt text](/assets/root.JPG " root ")

Figure 1. The Root path created in config.php

In Fig 1, with the help of google, I found the code to get back to the root directory at all times. The problem was when inserting the code into the link tag with PHP, it did not seem to find the path and it threw errors after errors. 

![alt text](/assets/css.JPG " CSS ")

Fig 2. Aaron suggestion to link to the CSS file

Aaron suggested using the code in Fig 2, which we tried at the beginning as it didn’t work before, why would it work this time, but it would not hurt to test. As this code has done many times before, it proved me wrong! It worked, what a surprise. The reason for us getting it to work is because the main.php builds up the admin page the same way as it builds the claim forms, if the CSS and images were not working for the admin tool, it would not work for the entire website.

Back to the important work, getting the admin pushing form name to the DB. 

![alt text](/assets/adminback.JPG " admin ")

Figure 3. The admin controller pushing data to the DB

I used a straightforward insert query and a bind param to push the data to the DB and then used JavaScript to display if the form had been added successfully.

![alt text](/assets/addingclaims.PNG " adding claims ")

Figure 3. The Forms table ready to work

Now we can start working on the claim forms and see what our problems are there when pushing to the database.
