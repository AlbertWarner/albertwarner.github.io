---
layout: post
title: Creating a Directory and the Problems involved
date: 2018-05-27 22:25 +1200
---

To explain the problem, I need to explain the reason for creating a directory in PHP. To solve some future problems, we thought it would be easier when the user uploads files such as images or documents, that this information was stored in a directory with the ACL number as the name. Rather than storing all the different claims form files in one directory and the user has to search to find what he’s looking for.

I used the <a href="http://php.net/manual/en/function.mkdir.php"> PHP manual website </a>, and it explained how to create a directory using PHP. This was actually very simple, all the command is doing is using a Linux command but in PHP. When I hardcoded the path “/home/se17group1/public_html/Data” there were no problems and the directory was created. This would not be a problem if we were using Kate to host the files, but the owner would move the files to a host server and the hardcoded path would not work. In the config.php we create a root path as shown in fig 1. We tested a few paths but came up with the same error, shown in fig 2.

![alt text](/assets/roottesting.JPG " root testing ")

Fig 1. Root testing in config.php

![alt text](/assets/permission.PNG " error ")

Fig 2. The permission denied error when using the root testing path

Wow, PHP really seems to be giving us an uphill battle, right when we require things to move smoothly. I spoke to Brett from the OP’s team and he came to help, and we went through every step slowly and we still got the same error as shown in Fig 2. But this time Brett reminded me that permission denied means that the PHP which is called www-data in Linux terms does not have permissions to create the directories on the server. Why did I not remember that, makes perfect sense? 

I went to Rob and he changed the permission as shown in Fig 3. 

![alt text](/assets/kate.PNG " kate ")

Fig 3. Rob changing Root permissions on Kate server

Unfortunately, it seems that PHP (www-data) still does not have enough permissions to create directories even though Rob made some extra changes. We can create a directory by copying pasting or right-clicking and creating a new directory but in Linux terms, which is what PHP is using to create the directory on the server, there is not enough permission for it to do so.    

I spoke to Adon and when the new server is setup for hosting the file, we can give those files more permissions and it should work but for now, we will upload files into one directory.

