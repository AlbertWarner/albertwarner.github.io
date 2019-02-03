---
layout: post
title: Database Reset
date: 2018-09-10 18:26 +1200
---

Well, this was a start to a major problem, welcome to reset a database anytime you want a problem. This would create major concerns especially if someone found the setup file and it was executed, the entire database would be deleted. 

Went into action and changed the create database controller. First, there is a query to check if there is a login details table exists and if true the second query checks if the admin user is available.

<h3>Database Checks </h3>

```php
$tablequery = "SHOW TABLES LIKE 'loginDetails'";
            $result = $pdo->query($tablequery);
            $tablecount = $result->rowCount();
            if($tablecount>0)
            {
              $adminQuery = "SELECT * FROM loginDetails WHERE ID='1'";
              $result1 = $pdo->query($adminQuery);
              $admincount = $result1->rowCount();
            }

```
If both these queries are true, then the user is redirected to a data found page

<h3>Database Checks </h3>
```php
else if($tablecount>0 && $admincount>0){
            include 'dataFound.php';
        }
```
This page asks for the Admin username and password. When correct the admin credentials are entered, all the tables are dropped, and new tables are created. The user is re-directed to the login page.  
