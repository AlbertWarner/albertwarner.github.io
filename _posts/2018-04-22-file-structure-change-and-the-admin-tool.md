---
layout: post
title: File Structure change and the Admin Tool
date: 2018-04-22 21:15 +1200
---

What have I done?

Did I think this was over, I was poorly mistaken. Time for some more changes and they make perfect sense. Hoping to get it sorted so the rest of the team can make the required changes to their pages.

The connect directory was changed to util directory and the clean.php, config.php and connect.php was stored here. The common directory with head and foot was moved to the views directory and the components were moved inside the forms. A bit of swopping and renaming. There was no problem with this, I thought with the previous big change, this would be easy.

While testing the new move, I thought the index page was not talking to the database and thought the new changes had caused a problem. I did some testing by echo “you are here” in the connect.php file and the config.php and to my surprise, the echoes were showing and it meant these files were talking no problem. I went even further by doing for loops to try print out the information being displayed. Answer: array [0] was the feedback I got. Spoke to Adon, maybe I was missing something, and 2 pairs of eyes are sometimes better than one. What was the problem, we went to check the database, to see if there was any data there, what a surprise to find the database empty? Arron had tasked Matt to create database file which created the database from nothing because currently we didn’t have one and the new server would require a database to be created. While creating this I think he might have accidentally wiped our current database clean and that includes the forms table, and therefore the index page had nothing to display. 

Adon suggested I create an Admin tool that would add forms to the database, just in case it happened again and in future if Derek had any new forms to be added he could use this tool to add new forms. The adding of new forms is way out of scope for now but the basic page is set up.

The admin tool was quick to set up because the main.php created everything, all I had to do was the format the middle section.

![alt text](/assets/admin.JPG " admin ")

Figure 1. New Admin tool page created

What are my Obstacles?

Not everything was working according to plan, as you can see in figure 1. The logo images are not displaying and the CSS is not applying to this document. When working with Adon, instead of having all those include directory path and then the file, we moved that all into the config.php file which would be included at the beginning, so all the files would know about include directories but only the files that required them would use them and the rest of the files would ignore them. This would reduce even more repetition in the files. 

![alt text](/assets/newinclude.JPG " include config ")

Figure 2. New include path created in config.php

![alt text](/assets/aircraftinclude.JPG " aircraft include ")

Figure 3. The new include path on the aircraft.php 

The original solution found at PHP manual did not seem to fix this problem when the file went to look for the image in the img directory under assets, the PHP believed it would find the assets directory under controllers. The new include shown in Figure 2, does not seem to go to the root directory and then move to directory required. Seems we have a problem. 

What do I want to achieve? 

Need to find a solution to make the files move from their current directory to the root directory and then look in the required directory for the file or image that is been requested.


