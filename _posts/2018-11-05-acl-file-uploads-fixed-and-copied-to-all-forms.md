---
layout: post
title: 'ACL File Uploads Fixed and Copied to All Forms '
date: 2018-11-05 21:11 +1300
---

We start off by grabbing Adon before having his coffee or getting into his office, I was intrigued to get this done and required help.

Adon wanted to use the form tags and let ajax push up the files using those tags. Unfortunately, I’m using the form tags for the other ajax call which uploaded the user data to the DB, which makes it look automated.

<h3>New Ajax Uploading Files </h3>
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

The changes we implemented was the for loop, looping around the uploaded files, which I remember doing in the tutorial guide that I found but this for loop was situated in the external JS file. Then we use Jquery to find the input field name and ACL number (this is used to change the files name to the input field name so that the client knows what files have been uploaded)

We used Jquery to grab the files that were uploaded with class name = form-parent.

<h3>New Input Fields </h3>
```php

<div class="form-group form-parent">
          <label class="control-label  col-sm-3">Pilots licence </label>
          <div class="col-sm-5">
            <input type="file" class="form-control" name="files[]" multiple>
            <input type="hidden" name="filenames" value="PilotsLicence">
            <input type="hidden" class="form-control" name="AclNum" value="<?php echo $ACLNUM?>" >
          </div>
  ```
The aircraft controller was not changed at all and it worked excellently. I copied the new ajax and controller information to all the other files. Then had to edit the input field, luckily most of the forms use the Aircraft’s files , so there were only a few modifications to do to other claim forms. This was bit boring but got it done.

<h3>Reflection </h3>

Nice to work with someone like Adon who can guide you and give you some help with more advanced technical work like ajax. Good day to get everything working.

