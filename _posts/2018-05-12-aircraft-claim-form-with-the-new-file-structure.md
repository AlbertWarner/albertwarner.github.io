---
layout: post
title: Aircraft claim form with the new file structure
date: 2018-05-12 23:49 +1200
---

With the admin tool working, do you think we might have some luck and have the aircraft claim form work just straight away? No, you are mistaken, let the new mission begin.

The index page was using the data from the DB no problem to display the forms. The index goes to the aircraft controller and that controller calls the main.php and the main builds the claim page, piece by piece. This was successful, and the page displayed with no problems until you had to submit the form to the DB.

![alt text](/assets/aircrafterror.JPG " aircraft error ")

Figure 1. The Aircraft error not pushing to the DB

This was an interesting one because if you read it, it didn’t seem to know what PDO is, this seems to be a connection problem. 

The second problem on that error was it didn’t seem to know anything about creating Person method, which is the method created in the models directory. This method pushes the data to the person table in the DB. 

What I thought would be the solution is putting the model.php in util directory and then include the connect directory in there and it would solve two problems at once. Because the new file structure goes from the index to the controller, then to the main page, after completion it goes back to the controller, I think the DB connection gets lost in this long route. I echo “Am here” in the person method and it would display meaning I was getting to the file but it was not pushing the data to the DB, meaning there was another problem.

I think at this point I was seeing too much PHP and needed to walk away from the problem. I spoke to Abdel and explained what I had done, and he took over the reins and tried to find the solutions.

