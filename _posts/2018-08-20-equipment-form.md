---
layout: post
title: Equipment Form
date: 2018-08-20 14:49 +1200
---

Wow did this form look super simple or have been I been looking at forms for days that I might be going a bit mad. Nope this form is super simple, and I got to use most of the components from the aircraft form with a few differences, but the client can look at the form and let us know if he wants a few changes. Matt will still need to go through the old forms and check them with the new ones. Don’t count your chickens before they hatch I always believe, the form was different in one major way, it had a repair or replace input field, but I had nowhere to store it. What did I do? I used the maintenance table in the DB and put the data in there.

 <h3>Update Extra fields into Maintenance Table in DB </h3>
 
```php

$aircraftID = clean_input($_POST['mainID']);
            $maintenanceType = 'maintenanceType';
            $description = 'description';
            $mDate = NULL;
            $designChange = clean_input($_POST['maintenance']);
            $description2 = 'description2';
            //Create an array
            $maintenance = array('aircraftID' => $aircraftID,
             'date' => $mDate,
             'maintenanceType' => $maintenanceType, 
             'description' => $description, 
             'designChange' => $designChange,
             'description2' => $description2);       
            //Insert data to the maintenance table
            updateMaintenance($pdo,$maintenance);
```

I had no extra queries to create or updates because all this was done already. I just used old code.

The form worked, and all data is pushing and displaying from the DB
