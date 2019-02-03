---
layout: post
title: Aircraft Pushing to the Database
date: 2018-05-12 23:52 +1200
---

Let us begin with a celebration of Abdel’s great work. I would never think that I could smile that much seeing data being pushed to the database. 

As I said in the <a href=" https://warnaa1.pages.op-bit.nz/2018/05/12/aircraft-claim-form-with-the-new-file-structure.html"> Aircraft claim form with the new file structure</a>, post, it seems to be a connection problem and did I hit the name on the head. 

This will be a bit long but the only way I can explain it, the index controller calls the aircraft controller, that controller calls the main and the main builds up the aircraft page by calling the different sections it required and makes the page look like an actual page. Then the user fills in his data and submits the data back to the controller which pushes the data to the DB but by the time it gets there, it seems to lose its DB connection. Abdel tested by adding the DB connection into the controller and it worked, data was pushed to the DB.

![alt text](/assets/problemsolved.JPG " problem solved ")
 
Figure 1. The database connection – this code is also found in the connect.php

We added the DB connect.php files to the controller’s directory and added an include at the beginning of the controller and all seems to work well, it might bite us later especially with Adon because I don’t think is supposed to work like this but maybe we will get a workaround at a later stage.

Abdel, Arron and I were having a discussion that the master repo on Gitlab needs to be updated with our new file structure because it was very behind, and we need to sort out any errors that might appear now before any more major changes happen. I updated the development branch from Albert’s branch and took the leap of faith. I pushed the development branch into the master branch and was I shocked when I saw the green tick to merge development into master and no errors…Say that again No errors, yes not one, the master accepted everything, and I didn’t need to remove anything.

![alt text](/assets/slack.jpg " slack ")

Figure 2. Slack message to the team with the successful changes

