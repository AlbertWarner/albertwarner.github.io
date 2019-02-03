---
layout: post
title: 'ACL Readme '
date: 2018-11-21 21:18 +1300
---

As mentioned before the documentation is just as important as the code. Here is the technical readme just in case someone new decides to take on this beast.

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

## File Path
```php
  ACL Directory

    -- asset
          -- css
          -- img
          -- js
    -- build
    -- controllers
         -- Models
         -- queries
    -- setup
    -- uploads - required permission (5777)
    -- util
    -- views
        -- common
        -- error
        -- forms
            -- components
                    - Aircraft
                    - Equipment
                    - HangarKeeper
                    - Libility
                    - Spray Liability
                    - SUV
                    -ThirdParty
        -- reports
```       
## Database Setup

1. In directory util there is a file called config.php and in the controllers directory there is another config.php
2. Open the file and you will find: $host , $userMS ,  $passwordMS , $database
3. Please note this file contains personal information to the Database, keep it safe on the server.
       - Information required to be completed by user:
       - $host -> The name of the database you are connecting to: mariadb.ict.op.ac.nz
       - $userMS -> The username you use to log onto the database
       - $passwordMS -> Password to the Database
       - $database -> The database used -> Please note: this must be manually created via phpmyadmin or via putty console.
4. Select setup Directory, click on Index.php
5. Database will be setup and ready to go.
6. Select the indexcontroller.php 

## Technical Report

1. Util/config
    - Has the directory paths used by the claim forms(views/forms/) to include different components required.
    - These are the paths to different files stored into variables, then you call the variable and it gives you the path
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

2. AccessControl1 -> has switch for different users logging in (users - admin, client, maint) and creates session 

    ```php
    switch($username)
    {
    case "admin":
    header('Location:indexcontroller.php'); #Where to go after a successful login. Header is like include but changes to that controller instead of adding it to the page
    break;
    case "client":
    header('Location:clientForm.php'); #Where to go after a successful login. Header is like include but changes to that controller instead of adding it to the page
    break;
    case "maint":
    header('Location:mainForm.php'); #Where to go after a successful login. Header is like include but changes to that controller instead of adding it to the page
    break;
    }               
    ```

3. indexcontroller takes the selected form id, get the form name and populates the database with empty rows, rows that the form requires 
    - Switch on form name 
    - Model form is included which calls different functions pages from the model directory
    - Each function creates empty row in the db
    - Primary Key is return and stored in variables ($contactID) , which are passed into different function if they require a foreign key  
    ```php
    switch($newpage)
    {
        case "aircraft":
            $contactID = createPerson($pdo,"Contact_Person");
            $engineerID = createPerson($pdo,"engineer");
            $pilotPersonID = createPerson($pdo,"pilot");
            $pilotID = createPilot($pdo, $pilotPersonID);
            $insuredID = createInsured($pdo,"Aircraft");
            $insurerID=createInsurer($pdo,$insuredID);
            $incidentID= createIncident($pdo,$insuredID,$contactID, $engineerID,$pilotID,$id,'0');
    ```

4. The indexcontroller calls the form controller from the /controllers directory

5. The controller has an if else statement to check if buttons on the form have been pressed.
    - Queries are done on the database to get the id's and any information required from the database.
    - Queries are stored in a file on /controllers/queries
    - The controller also checks which user is logged in
    ```php
    elseif(isset($client) ==true)
    {
        //code for the client
    }
     elseif(isset($MainClient) ==true)
    {
        //code for the maintenance user
    }   
    elseif(isset($admin) ==true)
    {
        //code for the admin       
    } 
    else
       //code for the admin
       include_once (dirname(__DIR__) . '/main.php');
    ```
    - Each user function call a different main.php (this is explained number 6)

6. Main.php builds up the claim pages piece by piece.
    - Common files such as head and foot are stored in views/Common
    - The variable passed from controller, allows the main to know which claim form to include between the head and footer
       ```php
       $page = 'aircraft';
       ```
    - The claim forms are stored in views/forms
    - Main has a variable called user and this variable is passed to the claim forms

7. The claim forms are build up by subsections
    - The sub sections are stored in views/forms/components
    - The variable user is used by a switch to define which user is logged in and what is seen by the different user
    ```php
    switch($user)
    {
    case "admin":                            
      <form id="aircraftform" class="form-horizontal" action="./controllers/aircraftController.php" method="POST" enctype="multipart/form-data">
        <div class="form-group">
          <label class="control-label col-sm-2" for="AclNum">ACL claim number</label>
          <div class="col-sm-3">
            <input type="text" class="form-control" id="AclNum" value="<?php echo $ACLNUM?>" Disabled>
            <input type="hidden" class="form-control" id="AclNum" name="AclNum" value="<?php echo $ACLNUM?>" >
          </div>
        </div>
        <!-- This user is sent to the controller to do a switch on when form is submitted -->
        <input type="hidden" class="form-control" id="contactID" name="userID" placeholder="" value="<?=$user?>">
        <!--URL -->
        <?php include_once ($formComponentUrl.'url.php');?>
        <!--Contact Details-->
       <?php include_once ($formComponentUrl.'contact.php');?>
    ```
8. The admin can click on the link on the index page. To Open the claim form. 
9. When the submit button is pressed on the claim form, the controller updates the information passed from the form to the DB
    - The controller includes models form which include different update models from the directory called models, same as 3 but updates instead of create
    - Models Are functions that either update or create fields in the DB
    - There is a switch depending that controls the users progress, admin is moved back to the index, client and maintenance are logged out.
    ```php
    switch($userID)
       {
           case "admin": 
                   $checkingValue = query_information($pdo,$incidentID);
                   if($checkingValue < 5)
                    {
                        $lastupdatestring = "ADMIN Updated Form ".$newUpdate;
                        $lastupdatenumber = 2;
                        $updateInfo = array('id' => $incidentID,'lastupdateBy' => $lastupdatestring, 'lastupdate' => $lastupdatenumber);
                        query_update($pdo,$updateInfo);
                    }                       
           include '../return.html.php';
           break;
           case "client":
                $checkingValue = query_information($pdo,$incidentID);
                if($checkingValue < 5)
                    {

                        $lastupdatestring = "Client Completed Form ".$newUpdate;
                        $lastupdatenumber = 3;
                        $updateInfo = array('id' => $incidentID,'lastupdateBy' => $lastupdatestring, 'lastupdate' => $lastupdatenumber);
                        query_update($pdo,$updateInfo);
                    }   
            //include '../return.html.php';//Remove just for testing
           include '../views/common/exit.html.php'; 
           break;
           case "maint":
                    $checkingValue = query_information($pdo,$incidentID);
                    if($checkingValue < 5)
                        {
                            $lastupdatestring = "Maint Completed Form ".$newUpdate;
                            $lastupdatenumber = '4';
                            $updateInfo = array('id' => $incidentID,'lastupdateBy' => $lastupdatestring, 'lastupdate' => $lastupdatenumber);
                            query_update($pdo,$updateInfo);
                        }   
           //include '../return.html.php';//Remove just for testing
           include '../views/common/exit.html.php'; 
           break;

    ```
    - The above switch also calls functions that update the DB, this information is displayed on the index page for Admin to see which user was last to update a form
    - Information for the numbers are the following: 1 - 2 is update by admin , 3 - update or submit by client and 4 - update or submit by maintenace
    - Number 5, if the PDF button is pressed this update with a 5 and if a client or maintenance open the link they are direct to a closed page. 

10. Ajax/jQuery on the All claim forms is working -> uses blur function to post to the DB
    - User does not need to save because the blur pushes all the time to the DB
    - The blur function user the form tag with id = "the forms name", everything between the form tag is seialize and sent to the controller
    
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
11. The PDF button calls the /build/ claim form being requested
    - Select Queries page is called and this get the information to display on the PDF

12. Populating the client or maintenance Link
    - This is populated in the controller and is only in the admin section
    - Take the server info breaks it into array, drops unrequired section and then creates a new path to form with different forms
    - This path is concatenated with Primary ID of the required form which is hashed 
    - Hash is stored in the DB and is compared to when the client opens the link

    ```php
     elseif(isset($admin) ==true)
    {
                    $url = (isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] === 'on' ? "https" : "http") . "://$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]";
                    $breakdown = parse_url($url); 
                    $schem = $breakdown['scheme'];
                    $host = $breakdown['host'];
                    $path = $breakdown['path'];
                    $path = explode("/",$path);   
                    unset($path[sizeof($path)-1]);
                    $path = implode("/",$path);
                    $Newurl = $schem."://".$host.$path;                                
                    include_once ($selectQueriesUrl . 'selectQueries.php');
                    $client = "/clientForm.php?id=";
                    $maint = "/mainForm.php?id=";
                    $directoryClient = $Newurl.$client.$hashedID;
                    $directoryMaint = $Newurl.$maint.$hashedID;
                    $page = 'aircraft';
                   // move to the home dir and find main.php
                   include_once (dirname(__DIR__) . '/main.php'); 
    } 
    ```
13. Display the information on the claim form
    - Every table is queried in the Select Queries file and this information is stored into variable
    - Painfully each variable is echo into the value tag of every input on the forms components 
    ```php
    <div class="form-group">
    <label class="control-label col-sm-2" for="insuredName">Insured</label>
      <div class="col-sm-8">
        <input type="text" class="form-control" id="insuredName" name="insuredName" placeholder="Enter insured" value="<?=$insuredName?>">
       </div>
    </div>  
    ```

14. File Uploads
    - Ajax pushes files to controller
    - input field has a id which the jquery get the information from.
    - push to uploads directory which needs permission of 5777 when set up

    ```php
        <script>
            $(document).ready(function(){
            $('body').on('click', '.upload', function(e){
                    e.preventDefault();
                    //var formData = new FormData($(this).parents('form')[0]);
                    var formData = new FormData();
                    var parent = $(this).parents('.form-parent');
                    var f = $(parent).find("input[type=file]");
                    for(var i=0;i<f[0].files.length;i++)
                    formData.append("files[]",f[0].files[i]);

                    var acl = $(parent).find("input[name=AclNum]").val();
                    var filenames = $(parent).find("input[name=filenames]").val();

                    formData.append("AclNum",acl);
                    formData.append("filenames",filenames);

                    $.ajax({
                        url: './controllers/aircraftController.php',
                        type: 'POST',
                        xhr: function() {
                            var myXhr = $.ajaxSettings.xhr();
                            return myXhr;
                        },
                        success: function (data) {
                            //alert("Data Uploaded: "+data);
                            alert("Files Uploaded ");
                            //below line still todo
                            //$(parent).find("input[type=file]").val("");
                            
                        },
                        data: formData,
                        cache: false,
                        contentType: false,
                        processData: false
                    });
                    return false;
            });
            });
        
        </script>
    ```

15. Archive button calls archive move controller
    - this controller calls a function which update a column with either 1 or 0 
    - 1 for archive
    - 0 for unarchive
    - foreach on the index page - if 0 display and on the archive page the same but if 1

16. Delete function and download images links calls different controller which display the images and allows for delete or download  
17. 3 User clients, maint and admin - the admin can update their password at any time but it affects all users
    - Update password controller - same as access controller but updates the password hashed
