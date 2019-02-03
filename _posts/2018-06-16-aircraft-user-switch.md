---
layout: post
title: Aircraft User Switch
date: 2018-06-16 01:29 +1200
---

I know this is not clean code, but it was a working idea at the time. The main problem is to get the information to display for the different users logging in. The aircraft controller has a variable that switches to true when a specific user logs in. There is a variable called $user which is stored in the main.php, this variable is passed to the aircraft.php where a switche is done on that $user variable. While this is not clean code, I copied the entire aircraft code 3 times, one for admin, client, and maintenance. The only difference is on the maintenance form there are fewer included sections than other 2 because the maintenance person completes less information than admin and client. I know it's not neat but glad it worked, which is awesome. Nice to see an idea work.      