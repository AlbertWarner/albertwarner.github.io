---
layout: post
title: 'ACL Archive part 2  '
date: 2018-10-23 21:15 +1300
---

In the first post, I just stated that I created the archive feature, and this just did a query on the database and displayed the information in a new tab called archive list. The whole reason for the archive list is for Derek to archive his old claim forms and I stated the best way to do this is by implementing a 1 or 0 feature.

First, I tested by creating a button feature, there would be a hidden input with the ID of the claim form stored in the name tag. When the button is pressed it would call a controller that would do an update query on a field in DB according to the claims forms ID passed through. Then use a select query to get information of that particular field in the DB and use an if statement to check if its 1 display on the index page and if 0 display on the archive page. 

This sort of worked because when I printed the ID from the controller, it did not print 1 ID requested, it printed all the ID's to screen. It could have something to do with the foreach that is used to display all the information to the user.

The solution is to use a feature that was already created for the admin form and client form. Both these pages get the ID passed to them and they do a query to get the form being requested and then display it to the user. I use this feature to pass the ID to a query that does an update to a column in the DB with either 1 or 0, let me show what I mean.

<h3>Archive Page Displayed to User </h3>
```php
<?php foreach($claimResult as $claimList){
                            $directory = '../adminForm.php?id=';
                            $directory2 = '../controllers/archivemove.php?id=';
                            $path = '';
                            if($claimList['archiveUpdate']>0){
                           ?>
                               
                            <tr>
                                 
                                <td> <?=$claimList['incidentID'];?></td>
                                <td> <?=$claimList['INSURANCENAME'];?></td>
                                <td> <?=$claimList['FIRSTNAME'];?></td>
                                <td> <?=$claimList['LASTNAME'];?></td>
                                <td> <?=$claimList['formID'];?></td>
                                <td> <?=$claimList['LASTUPDATEBY'];?></td>
                                <td> <?=$claimList['dated'];?></td>
                                <td > <a class="btn btn-info" href="<?=$directory.$claimList['incidentID']; ?>">Link</a></td>
                                <td > <a class="btn btn-info" id="archive" href="<?=$directory2.$claimList['incidentID']; ?>">Unarchive</a></td>
```

This page displays information from a query and displays it to user. The user selects the archive button which an input field been styled to look like a button. That calls archive move file with the incident ID of the form required.

 <h3>Archive Move File </h3>
```php
$directory = 'archiveController.php';
            $id = $_GET['id'];
            
            //select the form from the db based on $id hash
            $selectQuery = "SELECT * FROM incident WHERE id = '$id'";
            //get the name... everything else works fine
            $form = $pdo->prepare($selectQuery);
            $form->execute();
            $formpage = $form->fetchAll(); 
            $incidentID = $formpage[0]['id']; // retrieve the name from array 

            $updateQuery = "UPDATE incident SET
            archiveUpdate = '0',
            dateCreated = dateCreated
            WHERE  id = '$incidentID'"; 
            $stmt = $pdo->prepare($updateQuery);
            $stmt->execute(); 

            unset($_POST); 
            include $directory;
```

The archive move file gets the ID of the incident, which is actually passed through, don’t need the select query to store the incident ID into a variable but it worked so I left the extra step. Then I do an updated to an archiveUpdate column in the DB and call the controller. The controller will query the DB and display all information if the archiveUpdate column had 1 in it and on the index page it exactly the same set up, but it will display all the archiveUpdate column with a 0. 

This was cool watching this work, select a button and the entire field disappears from the page. I really enjoyed this.

<h3>Reflection </h3>
Interesting to see how old code could be used to fix this problem. To see if($claimList['archiveUpdate']>0) function work, inside the foreach loop was great. I did not test it before implementing but glad it worked. 