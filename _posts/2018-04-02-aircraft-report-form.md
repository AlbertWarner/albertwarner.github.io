---
layout: post
title: Aircraft Report Form
date: 2018-04-02 14:45 +1200
---

What have I done?

In the Post <a href=" http://warnaa1.pages.op-bit.nz/2018/03/25/index-controller-and-client-form.html"> Index Controller and Client Form</a> each member was allocated a report form to create. I chose to do the Index controller, Client form, and the aircraft report form. 

The report forms seemed easy at first because we could copy the aircraft claim form structure and paste it into the new form and removed and add fields as required. Following the examples of the report forms on the <a href=" https://www.dropbox.com/sh/zz9wq1i7zm5msmg/AAAbSQSqYEiexOSUf2v_5A0sa/Report%20templates?dl=0 "> DropBox Repo</a> got a bit complex. The forms seem to be all over the place and one of the big questions are: Why are the claim forms requesting so much information from Derek’s client but only uses some of the information to produce a report for the Insurance company. 

With that question on the side, I completed the Report form that looked almost the same as the examples but added a few extra lines. Derek will need to go through the report form and say what he wants to be added or removed, as Adon said if the changes become too much we can consider a generic report form for all the claim forms. 

![alt text](/assets/aircraftreport.JPG " aircraft report ")

Fig 1. The aircraft report form created and ready to send to Derek for feedback

Phase 1 is to be tested by Derek. He will enter data from his old claim forms and test the new forms. The database has a large amount of test data, dated back to last semester in Software Engineering. We need to clean the database so that Derek’s data is visible on the Index page, which Abdel created a query to display the data in a table. 

I started cleaning the database by using the empty option in phpmyadmin but found that foreign key constraints were causing problems for me to delete all the data. I had to go to a class but asked Abdel to look for me and he got most of the data removed. 

What are my Obstacles? 

No major Obstacles at the moment, just waiting to send the report form to Derek and wait for feedback. The interesting question I have is, what image does he want to display on the form. On the example is states “Assessor to add suitable photo”. I also need to clarify with the team if we were supposed to make the HTML form only or the controller as well, but I think the controller can’t be fully functional without the HTML layout been completed.

What do I want to achieve? 

Need to add a Hash column to the Incident table and have the incident ID hashed and storing to the Database. The hashed number will be a security feature so that people can’t change the number and look at other people’s claim forms.
