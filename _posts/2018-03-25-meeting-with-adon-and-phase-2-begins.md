---
layout: post
title: Meeting with Adon and Phase 2 Begins
date: 2018-03-25 23:43 +1300
---

With Adon and Aaron unable to be with us in the previous phase 2 planning, we showed them what was required to get the website functional according to what the client wanted. 

With Adon's guidance, he directed us in a way to move forward. We need to create a second controller almost the same as the index controller, but this controller is sent to the client and the HTML fields that Derek fills in are populated from the database. Leaving all the open fields for Derek’s client to complete. I must admit at this point I was a bit confused on what we were doing, trying to work it out in my head how this was all going to work and how on earth were all these pieces going to come together. 

![alt text](/assets/adonplan.JPG " Adon plan ")

Fig 1. Adon Going through the plan with us and showing what is required.

What have I done?

The plan was to create an empty incident table in the database. The incident table was the primary table joining most of the other tables together. We needed to create an empty field, this field would be updated every time Derek or his client put data into the database. The field wouldn’t be completely empty, the form ID will be inserted.

I started by creating the insert query on the index controller, my concern was on the incident table it has 2 foreign keys pointing to the insurance ID and the contact ID, but then checking again, the database is set up to receive NULL’s. This will allow us to put NULL’s when an insurance ID or contact ID is inserted into incident table.

![alt text](/assets/indexcontrollerplan.PNG " index controller plan ")

Fig 2. Insert query to enter only the form ID into the incident table, this how we will control further update queries

The incident table required a new column called Date Created, which is timestamped when the data was inserted, and this can also be used for record keeping. 

![alt text](/assets/insert.JPG " insert ")

Fig 3. Tested the insert query and testing if the time stamp is working

Adon sat with me and asked a few questions on the index controller. We drew up a plan on using JAVASCRIPT on the input button to stop the controller from executing. This would be neater code than having a large if statement on the index controller. Only one if else statement is required and the code looks cleaner.

![alt text](/assets/indexmainplan.PNG " Phase 2 plan ")

Fig 4. Javascript plan to stop the controller executing when the button is pressed.

What are my Obstacles?

No major obstacles at the moment, lots of planning to do. Which is great because then most of the people are in the same boat and understand what is happening.

What do I want to achieve?

Complete the Javascript on the button

