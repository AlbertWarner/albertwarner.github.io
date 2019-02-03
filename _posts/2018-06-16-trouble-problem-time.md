---
layout: post
title: Trouble, Problem Time
date: 2018-06-16 01:35 +1200
---

We struck one big problem when not needed. Abdel had been stuck updating the incident table for a couple of days and we did some pair programming and tried to get the incident table pushing. The whole day was bad, we could not figure out why it wasn’t updating the tables. I had to try and figure out why the form wasn’t updating, I started from scratch by creating the empty tables functions in the index controller and then went through each update functions one at time until I reached the incident update and with print_r() which is PHP way of displaying what is in an array. I found the names of the variable had been pushed by the array were not the same as the names pushing to the DB. The incident was working and updating the DB.

It was bit harsh starting from the beginning and not trying to work on Abdel’s code and figure out his problem, but I wanted to break the problem down and understand what had happened. Abdel was still working on his problem and hadn’t pushed the code to Gitlab and I couldn’t read his problems. I could have copied his code from kate and implemented it into my code and then worked out his problem. I am bit control freak and need to understand the problem before I can fix it, this could explain my reason for starting from the beginning. Secondly, maybe there was a problem with Abdel’s code and if I copied and pasted it, I might have copied a problem and would not be able to find a solution.
