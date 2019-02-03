---
layout: post
title: Ajax/jQuery
date: 2018-08-05 15:27 +1200
---

This was a fun learning experience. 


<img src="{{ 'assets/images/Project2/ajax.jpg' | relative_url }}" alt="ajax" />


Image 1. Ajax/jQuery pushing data to the DB with a submit button pressed

As you can see in Image 1, there is a lot of code commenting out because there were a few different trial and errors.

Two websites that helped resolve the problem was:

<a href="https://stackoverflow.com/questions/26523448/submitting-hidden-input-values-with-jquery-post-empty-db-columns-and-notice-u"> Stack Overflow 1</a>

<a href="https://stackoverflow.com/questions/36681132/jquery-post-all-form-data-onblur-from-specific-form"> Stack Overflow 2</a>

I didn’t understand the PHP serialize 100 % so I did some research and found Image 2 explained it nicely:

<img src="{{ 'assets/images/Project2/serialize.JPG' | relative_url }}" alt="serialize" />

Image 2. Serialized explained

On the controller end, there was a slight problem because the IF post "Submit Button" was not going to work because there wasn’t a button been pressed to save the data. 

I moved the if post “pdf button” to the top of the if-else statement meaning if the pdf button was pressed it created the pdf else post data to the DB. 

The Queries are working and data is pushing to the Database on blur function, which means when the user clicks out of the input field it pushes data to the DB

<h3>Reflection</h3>
Learned a lot about Ajax and how it takes the input data and post the information to the DB without a button been pressed. Very Impressed to see it work. The data sent is serialized data which is like a JSON file(Best way to explain it in my mind) being pushed to the controller.
