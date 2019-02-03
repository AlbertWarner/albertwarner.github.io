---
layout: post
title: Interesting Database Find
date: 2018-10-04 20:54 +1300
---

Was I mistaken on my previous post of everything working well? Small problem, every time a user opened a claim form, or the admin saved the form the date created column, which is a “timestamp” in MYSQL would update at the same time. I thought it was because we were using a date, time function of PHP and updating the table with it and this was causing the DB to update the column. I removed the PHP date function and still was doing the same thing. Good old Google to do some searching and see what I can find, stack overflow had the answer: <a href="https://stackoverflow.com/questions/2844863/mysql-updating-entry-without-updating-timestamp">Mysql updating entry without updating timestamp</a>. 

I took the easy option of the 3, just make the timestamp column equal itself, meaning the column will update with its original data every time the table is touched.

<h3>The user update working</h3>
```php 
$updateQuery = "UPDATE incident SET
            lastupdateBy = :lastupdateBy,
            lastupdate = :lastupdate,
            dateCreated = dateCreated
            WHERE  id = :id"; 
            $stmt = $pdo->prepare($updateQuery);
            $stmt->execute($updateInfo); 
```
 I remembered there was another update function on the incident table and this change the column as well, strange we didn’t notice it, but I fixed that function as well.
 
This was weird, the function was updating different columns on the table, but the timestamp column was updating, I must do some research into why this happens. I have it working but it will be interesting to see the reason.
