---
layout: post
title: Phase 2 Start the planning
date: 2018-03-18 17:05 +1300
---

What have I done? 

As stated in my previous post, Aleen helped me by looking at the code and fixing a few errors. The third party and some of the engine sections on the form were not pushing to the DB.

In the engine sections it was easy to find my mistakes, I had assigned incorrect “name” variables on the post on the controller. This fixed my problem and the engine sections was working.

On the third-party section, the form only asked for person details, with this information there is no way to know if that person is connected to a third party, so this information needs to be joined to the third-party table in the DB. Again, more information is required for the third-party table in the DB. Images below demonstrate this.

![alt text](/assets/liabthirdparty1.JPG " Liability third-party ")

Fig 1. HTML form of the third-party person

![alt text](/assets/thirdpartydb.JPG " Third-party DB ")

Fig 2. DB of the third-party table

Solution to the problem, as shown in Fig3, the variable is hard coded with the word Liability claim and when doing a search query, we should get the information required for the third-party.

![alt text](/assets/liabthirdparty.JPG " Third-party DB ")

Fig 3. How I got the information to push to third-party table

The liability claim form was tested, and all data is pushing to the database.

Abdel, Aleen and I spend the last hour of Thursday 15/03/2018 putting together the plan for phase 2. Fig 4. Shows the requirements for this website to be completed. From software engineering this is what I remember Derek’s requirements were.

 ![alt text](/assets/phase2plan.JPG " Phase 2 plan ")
 
Fig 4. Planning phase 2

What are my Obstacles?

Time, there is still a large amount of work to be done and I feel a large portion of this website will be out of scope for 3 people. Especially if new work comes in and team members are taken off to do other work.  

We have a meeting with Adon on the 19/03/2018 and will discuss what needs to be done to move forward.

What do I want to achieve?

Start working on the new report forms ASAP

