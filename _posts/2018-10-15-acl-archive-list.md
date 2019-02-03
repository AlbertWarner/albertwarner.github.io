---
layout: post
title: 'ACL Archive List '
date: 2018-10-15 21:03 +1300
---
This was easy in a sense, I created archive controller, that queries the database and the results are displayed in a table.

<h3>Query to display the archive page</h3>
```php 
$claimsReport = "SELECT incident.id as incidentID, 
                                insured.insuredName as INSURANCENAME, 
                                person.firstName as FIRSTNAME, 
                                person.lastName as LASTNAME, 
                                form.name as formID, 
                                incident.lastupdateBy as LASTUPDATEBY,
                                incident.dateCreated as dated  
                                FROM incident 
                                INNER JOIN form
                                ON incident.formID=form.id
                                INNER JOIN person
                                ON person.ID = contactID
                                INNER JOIN insured
                                ON incident.insuranceID = insured.id ORDER BY incidentID DESC" ;                                      
                //Prepare the select statement.
                $stmt = $pdo->prepare($claimsReport);
                //Execute the statement
                $stmt->execute();
                //Retrieve the rows using fetchAll.
                $claimResult = $stmt->fetchAll();
```

I copied the index page style to direct the user back to home page as shown in image 1.

![alt text](/assets/images/Project2/archive.jpg " Archive ")

Image 1. Archive redirect user home

I spoke to Matt and suggested we need to use this style for all the pages, to stick to a convention that looks neat. Not one page looks like this and the other pages look completely different, people might think they went to a different webpage. Matt agreed, and he will update the password page and uploading images pages to same style I have used.

The archive page is not finished, there needs to be a button added to an index page that allows the admin to send the claim form to the archive page and the reversal on the archive page. I was thinking of doing this with 0 or 1 sequence if 0 shown on the page and if 1 show on the other page and keep the 0 or 1 in the database an create a function to update the table. I will work on this.

