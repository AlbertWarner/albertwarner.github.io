---
layout: post
title: Liability Form
date: 2018-08-20 14:13 +1200
---

Can this day get any easier, wow this was quick work and 2 forms done in a day? Felt like a hack but it was straightforward, I viewed the old files of the Liability form and compared it to the Hangar Keepers and found them to be exactly the same, I copied all the hangar keepers form information to the liability form and did the same to the controller. The only difference was the heading on the forms. It worked, the form took me less than an hour to complete. 

But there were problems/bugs/errors amongst the daisy’s as shown in image 1.

<img src="{{ 'assets/images/Project2/errorslib.JPG' | relative_url }}" alt="errors" />

Image 1. Errors when the submit button is pressed

These errors above only happen when the submit button is pressed. The reason for them is a variable is looking for data to posted but nothing is passing through to the controller because 1 field is a drop-down box and the others are radio buttons. I did google search and check that radio buttons and drop-down boxes can display what was selected but I have a few more forms to completed and I asked Matt if he wouldn’t mind looking into this and getting it sorted. The rest of the form is working fine and ajax is pushing to the DB.
