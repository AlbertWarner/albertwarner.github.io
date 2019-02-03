---
layout: post
title: Select Queries Problem
date: 2018-09-03 14:52 +1200
---
The spray liability form is a very different form and only captures basically large comments and does not have an aircraft or equipment ID. The problem is on the query side because there are queries that use either the aircraft ID to get the information and if there is no number to submit to the query then it has an error. I fixed this problem by doing the following:

<h3>Aircraft Query Fix </h3>
```php

$generalQuery5="SELECT * FROM aircraft WHERE engineerID = ' $engineerID'";
            //Prepare the select statement.
            $stmt = $pdo->prepare($generalQuery5);
            //Execute the statement
            $stmt->execute();  
            $generalResult5 = $stmt->fetchAll();
            if(!empty($generalResult5))
            {
            $aircraftID = $generalResult5[0]['id'];
            }
            else{ $aircraftID = '0';} //Spray Liab don't use equipment or aircraft, make them 0 , so that other queries dont fall over
            }
```

Also, I went through all the queries and I added If (! empty ()) code, if the query comes back empty then the it will not proceed.

<h3>Problem 2</h3>

There is a query that the SUV form uses to gain 3 different equipment details from the DB using an associative table but there are other equipment queries just like this one but they only get one equipment detail. The error was because the query would ask for more details than a DB had for that ID being used. I know this is messy and could use one query for tables and use if statement to check. Will need to clean the code when all is working, for now, just focus on getting a working website for the client to use. How I fixed the problem used 3 checks in the if statement, if empty 1 && empty 2 && empty 3. 

Awesome to see these fixes work. 
