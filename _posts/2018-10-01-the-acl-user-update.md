---
layout: post
title: 'The ACL User Update '
date: 2018-10-01 20:51 +1300
---

One of the new features that Derek wanted was when a user opens the form and saves the document etc. The user that last updated the document would display on the index page. It will be a reference for him to check how far the client is with the form.

When I first created this feature it was easy,I created an extra Column in the incident table and created an updated query that would update which user had opened or save the document. Wow, was that it? ha-ha nope, showed it to Adon and he said it was ok but when the user creates a PDF, the client or the maintenance should not be able to view the page if they logged in at a later stage.

I thought a numbering system, would be the best path to solving this problem.

1 -2: Admin update or create a page

3: Client open claim form or submitted completed form

4: Maintenance open claim form or submitted completed form

5: Document completed, and PDF saved

Created a second Column in the DB and stored the number and a string every time a user opened or saved the document. 

So here is a breakdown of the code:

First, I create 2 functions, first function gets the number currently stored in the DB 

<h3>Select Query Function</h3>
```php 
<?php
 function query_information($pdo,$incidentID)
 {
        try{
        //  $incidentID = clean_input($_POST['incidentID']);
         $selectQuery = "SELECT lastupdate FROM incident WHERE id = '$incidentID'";
         $check = $pdo->prepare($selectQuery);
         $check->execute();
         $number = $check->fetchAll();
         $value = $number[0]['lastupdate'];
         return $value;
        }
        catch(PDOEXCEPTION $e)
        {
        $error = 'Select incident lastupdate error';
        include_once ('./views/error/error.html.php');
        exit();
        }
 }
?>
```

The second function takes an 2D array which contains a string value and a number value, which is updated to the database.

<h3>Update Function</h3>
```php 
<?php
function query_update($pdo,$updateInfo)
{
    try{
            $updateQuery = "UPDATE incident SET
            lastupdateBy = :lastupdateBy,
            lastupdate = :lastupdate,
            dateCreated = dateCreated
            WHERE  id = :id"; 
            $stmt = $pdo->prepare($updateQuery);
            $stmt->execute($updateInfo); 
    }
    catch(PDOEXCEPTION $e)
    {
        $error = 'Update incident lastupdate error';
        include_once ('./views/error/error.html.php');
        exit();
    }
}
?>
```
The first function gets a numeric value, and this stored in variable, then an if statement compares whether the variable is less than 5 then update function adds new information to the DB. If Derek has printed the PDF, then the DB is updated with the number 5. When the if statement is false the client/maintenance user is directed to closed page, but Derek can still access the claim form.

<h3>The user update working</h3>
```php 
 elseif(isset($client) ==true)
    {
        include_once ($selectQueriesUrl . 'selectQueries.php');
        $newUpdate = date("Y-m-d H:i:s");
        $checkingValue = query_information($pdo,$incidentID);
                if($checkingValue < 5)
                    {
                        $lastupdatestring = "CLIENT Opened Form ".$newUpdate;
                        $lastupdatenumber = '3';
                        $updateInfo = array('id' => $incidentID,'lastupdateBy' => $lastupdatestring, 'lastupdate' => $lastupdatenumber);
                        query_update($pdo,$updateInfo);
                        $page = 'aircraft';
                        include_once (dirname(__DIR__) . '/mainC.php'); 
                    }
                    else{
                        $page = 'closed';
                        include_once (dirname(__DIR__) . '/mainC.php'); 
                    }
        
    }
```

 Nice to see this working and doing what is required. This can be implemented on the other forms and should work well.

