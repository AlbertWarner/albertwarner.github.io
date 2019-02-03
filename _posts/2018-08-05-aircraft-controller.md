---
layout: post
title: Aircraft Controller
date: 2018-08-05 15:22 +1200
---

Over the holidays I found time to get most of the select queries working and these queries would display data from the database in the individual input fields on the HTML as a value. I found if the value was empty, the placeholder would display instead.

The problem here was there were a number of queries, they accumulated to about 500 lines of code and the code was required in 4 different places. That would be 2000 lines of unnecessary duplicated code.

I copied the code into a separate file, one called “Select Queries” and the other called “Select Queries Hash”. The reason for the two different files was because the client and maintenance, use the hash id in the queries, where the admin uses the normal table id.

On the aircraft controller where the queries would be required I used the following code:

include_once ($selectQueriesUrl . 'selectQueriesHash.php');

No problems and the queries worked fine, and data was displayed on the HTML forms where required.
