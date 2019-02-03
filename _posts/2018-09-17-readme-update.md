---
layout: post
title: Readme Update
date: 2018-09-17 18:39 +1200
---

The read me can be updated a bit further but a start. Adon suggested I changed it from readme.txt to README.md and then I can use mark down and even show some code for an explanation. I’m just putting the readme here cause its kind of important for another developer.  I had the password’s for the website and database in the readme which  I have removed, just to be rather safe than sorry.

<h3>README.md</h3>

{% highlight ruby %}
## Welcome To The Aviation Claims LTD website.

The Aviation Claims LTD website

Developers in Software Engineering:

- Betina Wendel,
- Scott McQueen,
- Tom Oborne,
- Phillip Hansen,
- Albert Warner

Developers in Project 1:

- Abdelrahman Hawwari,
- Aleen Kaye Barcos,
- Matthew Owens,
- Zoe McBride Andrews,
- Albert Warner

## Database Setup

1. In directory util, there is a file called config.php and in the controller's directory there is another config.php
2. Open the file and you will find: $host , $userMS ,  $passwordMS , $database
3. Please note this file contains personal information to the Database, keep it safe on the server.
       - Information required to be completed by user:
       - $host -> The name of the database you are connecting to: mariadb.ict.op.ac.nz
       - $userMS -> The username you use to log onto the database
       - $passwordMS -> Password to the Database
       - $database -> The database used -> Please note: this must be manually created via phpmyadmin or via the putty console.
4. Select setup Directory, click on Index.php
5. The database will be setup and ready to go.
6. Select the indexcontroller.php 

## Technical Report

1. Util/config
    - Has the directory paths used by the claim forms(views/forms/) to include different components required?

    ```php
    $formComponentUrl = dirname( __DIR__) . '/views/forms/components/Aircraft/';
    $formHelicopterUrl = dirname( __DIR__) . '/views/forms/components/Helicopter/';
    $formLiabilityUrl = dirname( __DIR__) . '/views/forms/components/Liability/';
    $formEquipmentUrl = dirname( __DIR__) . '/views/forms/components/Equipment/';
    $formHangarUrl = dirname( __DIR__) . '/views/forms/components/Hangarkeeper/';
    $formthirdpartUrl = dirname( __DIR__) . '/views/forms/components/ThirdParty/';
    $formSprayLiabilityUrl = dirname( __DIR__) . '/views/forms/components/SprayLiability/';
    $formSuvUrl = dirname( __DIR__) . '/views/forms/components/Suv/';
    ```

2. AccessControl1 -> has a switch for different users logging in (users - admin, client, maint) 

    ```php
                switch($username)
                {
                    case "admin":
                    header('Location:indexcontroller.php'); #Where to go after a successful login. The header is like include but changes to that controller instead of adding it to the page
                    break;
                    case "client":
                    header('Location:clientForm.php'); #Where to go after a successful login. The header is like include but changes to that controller instead of adding it to the page
                    break;
                    case "maint":
                    header('Location:mainForm.php'); #Where to go after a successful login. The header is like include but changes to that controller instead of adding it to the page
                    break;
                }
    ```

3. indexcontroller takes the selected form and populates the database with empty tables, tables that the form requires 
    - Switch on the form name
    - The model form is included which calls different functions pages from the model directory
    - Each function creates empty tables in the db  
4. The indexcontroller calls the form controller from the /controllers directory
5. The controller has an if else statement to check if buttons on the form have been pressed.
    - Queries are done on the database to get the id's and any information required from the database.
    - Queries are stored in a file on /controllers/queries
    - Reason for the above note -> if the admin completes any information on the form, that information must know where to go in the DB
    - The controller also checks which user is logged in
6. Main.php builds up the claim pages piece by piece.
    - Common files such as head and foot are stored in views/Common
    - The variable passed from the controller, allows the main to know which claim form to include inbetween the head and footer
    - The claim forms are stored in views/forms
    - Main has a variable called the user and this variable is passed to the claim forms 
7. The claim forms are build up by sub sections
    - The sub sections are stored in views/forms/components
    - The variable user is used by a switch to define which user is logged in and what is seen by the different user
8. The admin can click on the link on the index page. To Open the claim form. 
9. When the submit button is pressed on the claim form, the controller updates the information passed from the form to the DB
    - The controller includes models form which includes different update models from the directory called models, same as 3.1 but updates instead of creating
10. Ajax/jQuery on the All claim forms is working -> uses blur function to post to the DB
    - The user does not need to save because the blur pushes all the time to the DB
    
    ```php
<script>
        $(document).ready(function(){
        $( "input[type=text]" ).blur(function() {
            $.post('./controllers/aircraftController.php',$("#aircraftform").serialize(),function(response){
                                /* alert(response) */; });
            });
        });
</script>

    ```
	
{% endhighlight %}

