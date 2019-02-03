---
layout: post
title: Client Meeting
date: 2018-04-22 21:18 +1200
---

Arron, Abdel, Matt and I had a meeting with Derek. Arron wanted to update him on our progress and changes.

Arron explained to Derek we made a massive change in the file structure, which would be a massive advantage to move the functionality of the website forward.

A very important question of mine was answered in this meeting, that was with the report forms giving less output than the claim forms were requesting from the client. The magical answer is, the claim forms are the most important forms of the website, these forms need to be printed and sent with all their information completed by Derek’s client to the insurance company. The report form is for Derek’s analysis and his finding of the incident. He was happy for us to have the report form push to PDF and he could manipulate the report in word. NB the claim forms must print to PDF. 

This is extra work for Abdel because he was put in charge of the PDF converter and how it works etc. 

Derek also requested that every time a file is attached, an indication shows at the end of claims form that those files are attached. We made a change to this in software engineering, thinking it was irrelevant but with the claims forms now needing to be printed, it becomes very relevant. We were thinking we could have global Boolean that is made false from the beginning and when a file is attached change the Boolean is set to true and if the Boolean is true, make the progress bar show green for an attached file.

Arron went through all the claims forms and asked which sections would be important for the maintenance people to see. This will help us when making the user and if the user is a maintenance person, they will only be able to see certain sections. This was one of the main reasons for the file structure and file changes.
