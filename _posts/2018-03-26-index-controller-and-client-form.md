---
layout: post
title: Index Controller and Client Form
date: 2018-03-26 01:05 +1300
---

To start, we had Zoe and Matt join the ACL project because their project was moved to Software Engineering. Will be great to have them back and put them to work immediately before they are moved to another project. With phase 2 explained to them we sat as a group and discussed which member can do what. The Report HTML forms have to be made from scratch, with the extra manpower this would be a great opportunity to get that work out of the way.

![alt text](/assets/teamplan.JPG " team plan ")

Fig 1. The group plans which form they are doing and what is still required to make this a fully functional site

What have I done? 

This was a very interesting afternoon and loads of fun. To get started I was working on the Javascript to stop the button for submitting the query to the controller. Busy doing some research and didn’t notice Adon watching, he stopped and showed how the button should work. The plan had changed instead of using Javascript, we used jQuery. We found a website that helped us solve a problem we were having because the if the statement was working (we tested it by showing the information on the DOM) but the form was not submitting when the correct claim form was selected from the drop-down menu. 

![alt text](/assets/jquery.JPG " jquery ")

Fig 2. Solution to our JQuery problem and the button controls if the document proceeds or not

Thank you, Adon for the support and guidance.

Abdel joined me, and we started to work on the query to get the name of the claim form from the  DB, this would allow us to move from the index page to the page selected on the drop-down. The problem was the information was sitting in the array and we were trying PHP explode to gain the information out of the array and store into a variable. Adon to the rescue again and it was a simple fix as shown in Fig 3.

![alt text](/assets/array.JPG " array ")

Fig 3. Getting the information out of the array to be stored in a variable

We were then able to move from the index page to the aircraft claim form. 

Next, we used the insert query I created on Monday 19/03/2018 to insert the form ID into the incident table and return an ID, this ID was used to create the ACL number, and this was then displayed on the aircraft claim form.

![alt text](/assets/acl.JPG " acl ")

Fig 4. Creating the ACL number

I had to show off a little to Tom our security in the PHP, we are using binding paramotors and a clean code function. He was very impressed and noted we could do the clean code function with a library. But there was a loophole in the drop-down query, if you opened the DOM, a hacker could insert code into value on the HTML and this would pass to the query. Security will need to improve.

We moved onto the client form and reverse engineered the index controller select query to gain the information of which form to move to. The form gets the ID (We tested by inserting the ID in the address bar) and this does a query to get the form name and then moves to that form.

The images show how the code works.

![alt text](/assets/claim.JPG " claim plan ")

Fig 5. The claim form code

![alt text](/assets/clientform.PNG " Client form ")

Fig6. Showing the cleintForm.php not working but actually, it only requires the ID

![alt text](/assets/clientformwithid.PNG " client form with ID ")

Fig7. ID inserted into the Address bar and the aircraft claim form is found

What are my Obstacles?  

Not an obstacle, just a statement: Mind blowing how this code works and interesting and amazing to see it work. Still got a lot to do, the fun isn’t over yet.

What do I want to achieve? 

Hash the ID Number and created a hash column in the DB to store the hash. I need to create the Report HTML that was assigned to me.
