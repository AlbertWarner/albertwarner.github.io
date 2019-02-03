---
layout: post
title: Production Server Fixing Code Errors
date: 2018-09-13 18:31 +1200
---
There were 2 problems on the production server side, first was the access controller included a link to the clean input file and every time the access file is called it remembered that file. I copied the clean input function into the access controller, but I see that must have failed because Matt put a check to see if the function existed or not.

<h3>Clean Input Function </h3>

```php
if(!function_exists('clean_input'))
    {
        function clean_input($data)
        {
            $data = trim($data);
            $data = stripslashes($data);
            $data = htmlspecialchars($data);
            $data = strip_tags($data);
            return $data;
        }
    }

```
 
The second problem was the input tags that are not of type “text”, for example, the type date when it shows on the HTML it is “dd/mm/yyyy” and when this information pushes to the DB, the DB does not know what this is, so it will send an error.The fix for this was pretty simple, I used the !empty() check, what this does is, it checks if the post is empty, if true the post is stored in a variable else it puts NULL into the variable.

<h3>Clean Input Function </h3>

```php
if(!empty(clean_input($_POST['date'])))
            {$date = clean_input($_POST['date']);}
            else{$date = NULL;}
```

The only problem to this is, we will need to do this to all inputs that aren’t of type “text”. I’m sure it will be easier to do this with jQuery but will check later, for now, it works. Doing it on the server side rather than client side. 

The last problem was cleaning up the Session and making sure it was at the top of the page and cleaning any unnecessary code near it.

Well, what can I say, it awesome to see the website live and working! The aircraft page is pushing to the database and the links are working for the different uses and a pdf is created and populated with user data. Still, need to test the other pages and there are some errors on the update password page but Matt said he will handle those.

The webpage is live and working! A very good day!   
