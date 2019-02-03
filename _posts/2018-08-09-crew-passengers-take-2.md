---
layout: post
title: Crew/Passengers Take 2
date: 2018-08-09 12:28 +1200
---

So today was an interesting day, the Dynamically testing of adding extra crew was changed and stated to use a for loop instead of trying populate everything by pressing a button . I liked this idea because it made more sense. So technically what will happen is the user will select the total amount of passengers from the drop-down box. This number will be passed into the database and when the form is refreshed extra passenger input fields will appear for the user data to complete. On the backend, there will be another for loop that will capture the information and insert the data to the DB.

Here are some interesting issues and learning experiences:


<img src="{{ 'assets/images/Project2/frontendfor.JPG' | relative_url }}" alt="for loop1" />

Image 1. For loop used on the HTML to produce the extra input fields


<img src="{{ 'assets/images/Project2/backendfor.JPG' | relative_url }}" alt="for loop 2 " />

Image 2. For loop used on the controller to produce the extra post into variables

In image one, it was easy to do the for loop and have the fields populate but the problem came when trying to populate the value field on the HTML. How does the value field work? There is a query on the backend that gets the data. This data is stored in a variable and the variable is echoed in the value field. The problem was, on the DOM you could see the value field displaying the variable name but not the data. Stack overflow to the rescue: <a href="https://stackoverflow.com/questions/13912342/php-print-variables-in-for-loop"> php-print-variables-in-for-loop </a>.

Second Issue, on the backend I used a for loop to produce the post variables and the data would be put into a 2D array and then updated to the database. I know that I could have used a foreach loop but the number of passengers required by the client was a fixed amount. I decided that a for loop would do the same job. The problem was on the post variable names need to be incremented for example test = post[passengerID2] the passenger ID would need to be incremented. Stack overflow to the rescue again: <a href="https://stackoverflow.com/questions/6595774/getting-data-from-post-within-a-for-loop"> getting-data-from-post-within-a-for-loop </a>.

Something I found interesting was to remember the difference between empty and Isset. 

<a href="https://stackoverflow.com/questions/4559925/why-check-both-isset-and-empty/4560099"> why-check-both-isset-and-empty </a>

<a href="https://stackoverflow.com/questions/7191626/isset-and-empty-what-to-use"> isset-and-empty-what-to-use </a>.

<h3>Reflection</h3>
I learned instead of fixing some code that would have been complicated to fix but looked very neat on the front end. The simple path is sometimes an easier path. It was interesting to learn how to increment a variable in PHP with a for loop. The other thing I learned or remembered was the difference between empty and Isset
