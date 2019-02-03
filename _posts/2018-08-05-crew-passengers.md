---
layout: post
title: Crew/Passengers
date: 2018-08-05 15:31 +1200
---

This seemed to be an easy task but while working through it,it is a bit more complicated than first thought. The data pushes to the DB no problem, it updates the person and passenger tables in the DB. 

Here are the problems:

1)	When the user clicks on the add passenger field it is not displaying data from the DB, the value on the input tag seems to be blocked, and won’t display any text. The reason could be the origin jQuery code creates a clone of the original input fields, but those values are working no problem. Why is this important? the user might think they didn’t insert any data because no data is being displayed.

2)	If the user submits the form without populating any extra passenger’s fields, the controller throws a number of errors because it is looking for certain name tags to be posted but there weren’t any.

I have found a solution, but I might need to change the entire structure of the jQuery, my tests are working but I don’t know what it will look like on the claim form. Will have to test and see. 

Here is link to me testing: <a href="http://kate.ict.op.ac.nz/~se17group1/Development/AlbertTesting/testing/index1.php"> Dynamically Testing</a>         


