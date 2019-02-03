---
layout: post
title: Spray Liability controller
date: 2018-03-12 12:10 +1300
---

What have I done? 

The Spray Liability Controller had to be created from scratch. I used the aircraft controllers structure as a model to work from. A few modifications were required because the spray liability needs to push to the farmer table in the database. 

Created the farmer owner and farm manager to push new people to the database.

![alt text](/assets/sprayFarmer.PNG "farmer created")

Fig 1. Farm owner and Farm Manager creating new people in the database

Created the comments section the push circumstances and property damage to the database. 

Testing of the spray liability pushing all fields to the database without any errors.

![alt text](/assets/testingSpray.JPG "Weather code done")

Fig 1. Spray Liability pushing to the database – used a var_dump to show the above output

![alt text](/assets/dbspray.JPG "Weather code done")

Fig 2. Phpmyadmin showing data in the database – above is the persons table

Excluding the obstacle below, spray liability is completed.

What are my obstacles?

All fields are pushing to the database excluding one field, the comments section. Checked the prepared statement variable binding and all seems to be in order.

Task: Will ask a team member to look at my work, maybe they see something I have missed.

Want to achieve?

Complete the Liability form.

