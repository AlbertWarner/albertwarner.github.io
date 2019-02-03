---
layout: post
title: Hangar Keepers Form
date: 2018-08-17 19:12 +1200
---
To start off, this seemed to be a straightforward form, most of the work had been completed in the aircraft form and helicopter form and I could copy that work into this one. It would not be that easy. I started off by opening an older version of files, just in case some of the forms were changed and the forms looked incorrect. When our client Derek looks at the forms, he can give us feedback about the forms, if they are incorrect or if there are changes to be made.

On the index controller, I add the functions to create empty columns in the DB for the Hangar Keeper to update.
<h3>Index Controller </h3>
```php
case "hangarkeepers":
                    $contactID = createPerson($pdo,"Contact_Person");
                    $engineerID = createPerson($pdo,"engineer");
                    $pilotPersonID = createPerson($pdo,"pilot"); //no owner table but pilot is used to connect equipment ect
                    $pilotID = createPilot($pdo, $pilotPersonID);
                    $insuredID = createInsured($pdo,"Hanger keepers");
                    $insurerID=createInsurer($pdo,$insuredID);
                    $incidentID= createIncident($pdo,$insuredID,$contactID, $engineerID,$pilotID,$id,'0');
                    $equipmentID = createEquipment($pdo,$incidentID,"Hanger_keepers");
                    createEquipment($pdo,$incidentID,"Component");

```
As you can see in the above comment there wasn’t a spot for Owners details in the DB, but a small light Bulb of an idea appeared to me. The DB has an incident table which requires a pilot ID, this allows the incident to know who the pilot is, but this form does not require the information of the pilots, so I used the pilot table to hold the owner’s details.
While updating the claim form I noticed most of its fields were exactly the same as the aircraft form

<h3>Hangar Keepers Claim Form </h3>
```php

		<?php include_once ($formComponentUrl.'url.php');?>
         <?php include_once ($formComponentUrl.'contact.php');?>
         <?php include_once ($formComponentUrl. 'insuranceDetails.php');?>
           <!-- Aircraft/ Component Liability Details Section-->
        <span class="anchor" id="anch3"></span>
        <h2 class= "text-center">Aircraft / Component Liability Details</h2>
            <?php include_once ($formHangarUrl.'component2.php');?>
            <!-- Aircraft owners contact details Subsection-->
            <h3 class= "text-center">Aircraft owners contact details</h3>
            <?php include_once ($formHangarUrl.'owner.php');?>
           <!-- Maintenance Being Performed Subsection-->
            <h3 class= "text-center">Maintenance being performed</h3>
             <?php include_once ($formLiabilityUrl.'maintenance.php');?>
  
```
In the above code you can see the $formComponentUrl points to the aircraft components and even the $formLiabilityUrl points to the Liability components. I found the components already created in liability for maintenance section, so I thought a good win for me I don’t need to create much. The only 2 sections that were required was components and owner’s details.
The Controller was also straightforward because I copied most of the variables and post information from the aircraft controller, just needed to do some modifications for component fields and for the owner fields, I copied the pilots(which was used to push the owners data)update person from the aircraft controller.

<h3>Component Query </h3>
```php
//Get the Component details
$generalQuery29="SELECT * FROM equipment JOIN incidentEquipment on equipment.id = incidentEquipment.equipmentID 
WHERE incidentEquipment.incidentID=$incidentID AND equipment.name = 'Component'";
//Prepare the select statement.
$stmt = $pdo->prepare($generalQuery29);
//Execute the statement
$stmt->execute(); 
$generalResult29 = $stmt->fetchAll();
if(!empty($generalResult29)){
$componentID = $generalResult29[0]['id'];
$airTypeC = $generalResult29[0]['type'];
$airMakeC = $generalResult29[0]['make']; 
$airModelC = $generalResult29[0]['model'];
$airSerialNumC = $generalResult29[0]['serialNum'];
$airYearOfManufactureC = $generalResult29[0]['yearOfManufacture'];
$descriptionCom = $generalResult29[0]['description'];
$manufacturer = $generalResult29[0]['manufacturer'];
```
In the Select Queries file, I added the above code to get data to display in HTML components.
Testing problems
When testing I tried to create a Hangar Keepers form and hit errors. The names of the forms were not aligning up with what was in the database. On the index controller, there is already a query that gets the form name and does a switch on that name, I echo it out and got Hanger Keepers, but the forms are called Hangar Keepers. Someone must have been thinking about their washing instead of a Hangar. I changed the pages.csv which is a file been read in when the database is created. I manually changed the DB because Matt was still working on PDF’s and required some data. Everything worked great.
