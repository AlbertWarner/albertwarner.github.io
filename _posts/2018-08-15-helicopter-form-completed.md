---
layout: post
title: Helicopter Form Completed
date: 2018-08-15 14:26 +1200
---

This was a good day but also an interesting day at the same time. I fixed errors stated in “Helicopter controller” post. The aircraft and helicopter are using the same select queries file, but the helicopter does not store any information for Left propeller etc, meaning there is no data for this query to produce, to stop this from happening, I added if (! empty) to the query as shown in image 1. 


<img src="{{ 'assets/images/Project2/empty.JPG' | relative_url }}" alt="Helicopter" />


Image 1. Select Queries Fix.

The interesting part of the day was, my teammate from last semester broke up the sections of the helicopter form differently to the other forms. Meaning I would need to include an unnecessary extra hidden ID’s to pass to the controller. I did try to use that form, but I found it to be a lost hope and unnecessary time wasted. I compared the aircraft form to the helicopter and found them to be exactly the same just different headings. I thought no way it could be this good, what is the meaning of this, the helicopter form in build up by different sections and instead of including the sections already created for the form, I will just use the aircraft form sections. Image 2 has a demonstration of the above meaning.  


<img src="{{ 'assets/images/Project2/heliForm.JPG' | relative_url }}" alt="Helicopter" />

Image 1. Using Aircraft Claim form sections to build the Helicopter claim form page.

This worked perfectly, the Helicopter form is pushing to the DB and data is showing on the form without any troubles. I ask Matt if he could look at the old Helicopter form and compare it to the working one, just to double check if I made any mistakes or if there are any fields missing.

<h3>Index Controller Populating DB</h3>
<pre><code>
case "hangerkeepers":
                    $contactID = createPerson($pdo,"Contact_Person");
                    $engineerID = createPerson($pdo,"engineer");
                    $pilotPersonID = createPerson($pdo,"pilot"); //no owner table but pilot is used to connect equipment ect
                    $pilotID = createPilot($pdo, $pilotPersonID);
                    $insuredID = createInsured($pdo,"Hanger keepers");
                    $insurerID=createInsurer($pdo,$insuredID);
                    $incidentID= createIncident($pdo,$insuredID,$contactID, $engineerID,$pilotID,$id,'0');
                    $equipmentID = createEquipment($pdo,$incidentID,"Hanger_keepers");
                    createEquipment($pdo,$incidentID,"Component");

</code></pre>
