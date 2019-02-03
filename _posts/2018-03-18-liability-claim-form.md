---
layout: post
title: Liability Claim Form
date: 2018-03-18 16:59 +1300
---

What have I done?

Abdel notified me about a part of the aircraft controller that was not pushing data, these fields were the Aircraft-Flight Details and I went through the aircraft controller and added the insert query. Thank you, Abdel. 

![alt text](/assets/flightdetails.JPG " Flight Details ")

Fig 1. Aircraft-Flight Details insert query pushing into the Database

Last week I had a problem with the comments not pushing to the database and an Undefined index error every time. I could not understand this because I used the code from the aircraft controller and it was working fine. Checked my code so many times and tested by hard-coding strings to push to the database, that seemed to work, but when I added the post data it kept getting Undefined index errors. 

Solution to my problem.

To my surprise, Grayson and myself were talking about the problem and we went through the HTML document and was I surprised to find the spray liability form has more than 2 text area input fields, there were 6 fields and I was only trying to push 2 of the 6 fields. I quickly coded up the 4 extra fields and tested them. Surprise, surprise it worked and all the comment fields were pushing to the database. Interesting that the extra fields that weren’t working, was stopping the data being pushed to the database.

![alt text](/assets/spraydb.JPG " Spray Liability DB")

Fig 2. Testing spray liability form comments pushing to the database

![alt text](/assets/sprayliab.JPG " Spray Liability ")

Fig 3. One of the four comments inserts query that I missed. This caused the undefined index error

Abdel and I were discussing how the models worked because in a small way it seemed a difficult process. In the Fig4 diagram below it shows how the data goes from the HTML to database. I suggested it will need to change because the controller will need to be called to produce an ACL number, which will be the number that we control all the forms. The controller should control which form is been shown but this can be discussed in phase 2 planning.

![alt text](/assets/layout.JPG " Talking ")

Fig 4. Abdel and I discuss how the data goes from the HTML to the database.

I started the Liability claims controller, there was a base controller already set up and I tested it to see if anything was working, unfortunately, I was not so lucky and no connection to DB could be made. I started by adding try catches to all the code to get the controller talking to the DB. The liability form was a tricky form because it was completely different to the normal forms I had been working on but I progressed on and got the first person to be added to the DB.

What are my Obstacles? 

![alt text](/assets/liaberror.JPG " Liability error ")

Fig 5. Maintenance section not adding to the DB 

I hit a major problem, there are 2 maintenance sections that need to push to the DB but the maintenance field in the DB required an aircraft ID, but the liability form isn’t about an aircraft, it is about the aircraft components or damaged components that a vehicle was carrying for an aircraft. The aircraft field also required a pilot ID. 

Solution to my problem, I created insert queries to the DB to insert a pilot and an aircraft, but I hardcoded the word “Liability claim form details” to each field that took a string, and this created the ID I required for maintenance information to be inserted into the DB

![alt text](/assets/liabdbmain.JPG " Liability DB Maintenance ")

Fig 6. Maintenance table in the DB

I still had a few errors of data not pushing to the DB, so I asked Aleen if she could help me and have a look and see if what I was doing wrong. She found some of my errors and corrected them but there were a few errors still appearing.

The Liability requires data to be pushed to the third-party field but the third-party table in DB requires more information than on the Liability claim form. 

What do I want to achieve?

Completed the Liability claim form pushing to the DB

