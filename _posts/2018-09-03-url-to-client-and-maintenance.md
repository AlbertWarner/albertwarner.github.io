---
layout: post
title: URL to client and Maintenance
date: 2018-09-03 14:56 +1200
---

This was an interesting but frustrating day, I got the full path I have been looking for, thank you <a href="https://stackoverflow.com/questions/6768793/get-the-full-url-in-php "> Stack Overflow get the full url</a>.

<h3>Output from above code from Stack Overflow </h3>
```php

http://kate.ict.op.ac.nz/~se17group1/Development/AlbertTesting/NewACL/AviationInsurance/ACL/adminForm.php?id=55
```

Yes, success but I need the “adminForm?id=” to be removed so that I can concatenate the “clientForm?id =” or” maintForm?id=”. This was a bit more complicated than thought, I was trying weird stuff and not getting it to work. 3 hours later, Martian came to see how we were doing and I explained the situation, he said maybe try split it on the “/” but then in the joining I was losing slashes etc and then he suggested substring. <a href="http://php.net/manual/en/function.substr.php"> PHP manual substring</a> thanks for the help Martian. This worked but ran into another problem if the id became large than 99 the substring would only remove a fixed amount of characters and this would cause an error if any characters were left behind.

Spoke to Adon and explained what happened and he suggested the same thing with the array and he came to help.

PHP has <a href="http://php.net/manual/en/function.parse-url.php"> Parse URL</a> which breaks up an URL into an array and it is very neat. You can get the hostname the path all broken up into an array. The problem with the path it was the full path which includes a few slashes and it might do on the production server as well, will be interesting to test. We used PHP explode to break up the path into another array and then we used <a href="http://php.net/manual/en/function.unset.php"> PHP uset</a> to remove the last number of the array which would hold the “adminform.php” which we wanted to remove.

We used PHP implode to join the array back together with slashes. Tested it and it worked. Super excited to see it work and it was fun.

<h3>Full URL code </h3>
```php

$url = (isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] === 'on' ? "https" : "http") . "://$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]";
                    $breakdown = parse_url($url); 
                    //var_dump($breakdown);
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
  ```

<h3>Reflection </h3>
Learning the new features such as the parse_url method breaks the url down in sub sections and the exploding the data into a array and removing the last slot of the array and then implode the data back together and it will always get right url was a great learn and fun peer programming with Adon, thank you. 
