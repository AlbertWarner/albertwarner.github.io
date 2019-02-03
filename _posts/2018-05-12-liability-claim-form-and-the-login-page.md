---
layout: post
title: Liability claim form and the Login Page
date: 2018-05-12 23:55 +1200
---

With the success of changing the aircraft claim form, I thought I would put in a little extra help and change the Liability form quickly, then move onto the more important work, like create the hashing of form ID and store it in the database, note this was what I want to achieve question which I answered about 3 weeks ago.

Did I just notice something that might create even more work for us? When the data is passed in POST to the controller via the name variable on the HTML, this variable is unique to each form and most of the claim forms are different, some in a small way, some in a large way. Meaning when we broke up the aircraft form into smaller sections, for example, the contact.php, we will have to split the other forms up and store them in their own directory. Otherwise, each form might not work. We will have to go through the files and check which name are the same but for now, we are splitting the form individually into their own sections and storing them under the common directory under the forms name. 

I split the form up, a bit of long tedious process cutting and pasting but as always, I made a mistake and the form was not pushing to the DB, I create a rightpropeller.php twice when there was supposed to left and a right propeller form. I corrected the mistake, and all worked fine.

Matt was assigned the login page, but he was having a problem with the HTML page going to the controller and the controller was looking for the connect file in the controller class. First, I suggested to Matt that we use the access controller like in web 2 which created a session. Then we can control the user logged in. I send him all the files via slack.

![alt text](/assets/loginpage.JPG " login page ")

Figure 1. The login page that Matt and I worked on

![alt text](/assets/login.JPG " login page ")

Figure 2. The access controller that Matt and I created

First, we got the login.php to see the CSS in asset directory, I did the same code that Aaron helped me with the main.php and it worked. The login in page worked fine. While testing the login page by entering user data, it reached the access controller but when it was a wrong username or password, the access controller would call the login page again but it lost connection to the CSS. One thing I have noticed, PHP does not like moving to a different directory. I think its because we are calling it wrong. I might go speak to Dale about this and get some advice.

So I suggested we move the login into the root directory and all seem to work with no problem, the login page worked and used data from the database to give access to the index page.
