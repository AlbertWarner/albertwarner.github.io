---
layout: post
title: Spray Liability
date: 2018-08-23 14:38 +1200
---

I was hoping the form would go smooth and be an ok build, but the Spray liability claim form was hugely different to the others. I copied the sections that were common to the aircraft but the following components I had to create:

<h3>Components created </h3>
```php

<?php include_once ($formSprayLiabilityUrl. 'incident.php') ?>
        <?php include_once ($formSprayLiabilityUrl. 'farmowner.php') ?>
        <?php include_once ($formSprayLiabilityUrl. 'farmManager.php') ?>
        <!--Weather Details-->
        <h2 class="text-center">Weather details</h2>
        <?php include_once ($formComponentUrl . 'weatherDetails.php');?>
        <!-- Circumstances of the incident Section-->
        <span class="anchor" id="anch5"></span>
        <h2 class= "text-center">Circumstances of the incident</h2>
        <?php include_once ($formSprayLiabilityUrl. 'circumstances.php');?>
        <!-- Property Damage Section-->
        <span class="anchor" id="anch6"></span>
        <h2 class= "text-center">Property damage</h2>
        <?php include_once ($formSprayLiabilityUrl . 'propertyDamage.php');?>
        <h2 class= "text-center">Hold Liability Letter</h2>
        <?php include_once ($formSprayLiabilityUrl . 'holdLiability.php');?>
        <h2 class= "text-center">Environmental Damage</h2>
        <?php include_once ($formSprayLiabilityUrl . 'environmental.php');?>
        <h2 class= "text-center">Personal Injury</h2>
        <?php include_once ($formSprayLiabilityUrl . 'personalInjury.php');?>
        <h2 class= "text-center">Statement to Owner</h2>
        <?php include_once ($formSprayLiabilityUrl . 'statementOwner.php');?>
        <h2 class= "text-center">Statement to CAA</h2>
        <?php include_once ($formSprayLiabilityUrl . 'statementCAA.php');?>
        <h2 class= "text-center">Statement to Police</h2>
        <?php include_once ($formSprayLiabilityUrl . 'statementPolice.php');?>
        <h2 class= "text-center">Statement to TAIC</h2>
        <?php include_once ($formSprayLiabilityUrl . 'statementTAIC.php');?>
 
```

After creating each component, I had to create the queries to display their data.

<h3>Queries Created </h3>
```php

//comments details - spray Liab
                                            $generalQuery35="SELECT * FROM comments WHERE incidentID =$incidentID AND commentType = 'Hold_Liability_Letter'";
                                            $stmt = $pdo->prepare($generalQuery35);
                                            $stmt->execute();  
                                            $generalResult35 = $stmt->fetchAll();
                                            if(!empty($generalResult35)){
                                            $holdID = $generalResult35[0]['id'];
                                            $holdComment = $generalResult35[0]['comment']; 
                                            }}

```

I really think I could have done the queries better, for example, I could have added an associative table from incident to comments and this would have given me the ability to create one query to populate an array and get the information out of the array. Instead, I created a query for each individual component. I did a test with a single query, in the arguments of the query I added “&& commentType = ‘environmental’” etc but the array printed out was filled with large amounts of duplications.

<h3>Update Function </h3>
```php

function  updateHLComment($pdo,$comment)
    {           
           $updateQuery="UPDATE comments SET  
            comment = :comment
            WHERE id = :id AND  commentType = 'Hold_Liability_Letter'"; 
           $stmt = $pdo->prepare($updateQuery);
           $stmt->execute($comment);
    }
```

With the un-neat way of doing the comments, which meant the function to update the DB were going to be un-neat as well, instead of creating 1 update function, I had to create 8 functions. I feel this is very un-neat and needs fixing but for now it is working, and it can be changed when code is being cleaned up.

The form is working, and no errors are showing. More Testing will be done at the end.