---
layout: post
title: ACL File Uploads
date: 2018-10-29 21:05 +1300
---

This was an interesting start, we had a problem with the file uploads :

1)	They did not allow multiple files to be uploaded 

2)	They got the name of the input fields but would overwrite each other when a new file was uploaded because they had the same name. 

3)	Every time a user wanted to upload a file or files, they had to press the submit button, this functionality was not good, the client or maintenance user would need to log in multiple times because when they submit a claim form, they are logged out automatically.


I found online <a href= "https://www.taniarascia.com/how-to-upload-files-to-a-server-with-plain-javascript-and-php/"> how to uploads files to a server guide </a>. This helped a lot and the guidance to use a for loop on the PHP to upload files was really helpful. 

   <h3>File upload in php -Aircraft Controller </h3>
```php

$errors = [];
            $AclNum = clean_input($_POST['AclNum']);
            $Inputname = clean_input($_POST['filenames']);
            $path = '/uploads/';
            $rootDir = (dirname(__DIR__));
            $extensions = ['jpeg','jpg','png','pdf','docx','xlsx','JPEG','JPG','PNG','PDF','DOCX','XLSX'];
    
            $all_files = count($_FILES['files']['name']);
            
            for ($i = 0; $i < $all_files; $i++) {  
                $file_name = $_FILES['files']['name'][$i];
                $file_tmp = $_FILES['files']['tmp_name'][$i];
                $file_type = $_FILES['files']['type'][$i];
                $file_size = $_FILES['files']['size'][$i];
                $tmp = explode('.', $file_name);
                $file_ext = strtolower(end($tmp));
                //$file_ext = strtolower(end(explode('.', $_FILES['files']['name'][$i])));
               
                $newName = $Inputname . "($i)";
                //$file = $path. "studentinfo($i).".$file_ext;
                $file = $path. $newName .$file_ext;

                $file = $rootDir . $path . $AclNum . "-" . $newName . "." . $file_ext;
    
                //$file = $path . $file_name;
    
                if (!in_array($file_ext, $extensions)) {
                    $errors[] = 'Extension not allowed: ' . $file_name . ' ' . $file_type;
                }
    
                if ($file_size > 5242880) {
                    $errors[] = 'File size exceeds limit: ' . $file_name . ' ' . $file_type;
                }
    
                if (empty($errors)) {
                    move_uploaded_file($file_tmp, $file);
                    //chmod($file,0770);//Sets the persmissions of the uploaded file so it can be deleted
                }
            }

```
With the guide, we set up a nice button for each upload section and it was working great, uploading multiple files to the server. This was working on my test but then I moved it to the actual ACL forms there are multiple upload sections and it all failed, nothing worked, the external JS file that I created like the guide indicated didn’t work, it all fell over.

I tried a few ways on the net but eventually I asked Adon and he help find the link to <a href="https://stackoverflow.com/questions/19295746/how-to-upload-multiple-files-using-php-jquery-and-ajax"> uploading files using ajax ,php , jquery </a>

<h3>Ajax Uploading Files </h3>
```php
  <script>
    $(document).ready(function(){
    $('body').on('click', '.upload', function(e){
            e.preventDefault();
            var formData = new FormData($(this).parents('form')[0]);
            var formData = new FormData();  

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
                    $(parent).find("input[type=file]").val("");
                    
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

Ajax to the rescue again, this was awesome the files were uploading but my fun would not last for long I copied the new uploads section to another uploads field and to another and thought let's test this. What a disappointment, after attaching files and pressing the uploads button nothing happened, but if I pressed the very first upload button I created, all the files would upload but with the wrong name. I spoke to Adon and we would look into the problem asap.

<h3>Reflection</h3>

Great learning how to use ajax to upload files and see it working, even though it is not correct. Almost there. The guide I found was good and informative. Solved all 3 problems at the beginning of the post in 2 days, good feeling getting things almost completed. 
