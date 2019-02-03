---
layout: post
title: Jekyll Installation
date: 2018-02-21 17:31 +1300
---

First post of 2018 for Project 1.  So, Jekyll has been interesting since Monday 19/02/2018. Removing my Software Engineering profile from <a href="https://gitlab.op-bit.nz/"> GITLAB</a> was a bit sad because I’m not able to implement it into the new site but I will find a way. Software Engineering was an interesting learning experience and I would like it to be noted in my work. Getting back to the reason for my first post being about Jekyll. You would think because I’ve done it a few times in Software Engineering, I would actually know in a small way how this software worked, was I mistaken!

Following the simple instructions which were given by Adon to install <a href="https://opbitproject.wordpress.com/project-assessment/"> Jekyll</a>, worked last semester but somehow it is not working this time. A step in the instructions: ‘gem install Jekyll bundler’ would fail every time. The reason for this was, the version of  Ruby 2.5.0-1 that I was using from the <a href="https://rubyinstaller.org/downloads/"> Ruby Website</a>, stated: “However, not all gems are maintained. Some older packages may not be compatible with newer versions of Ruby and RubyInstaller.”
 
I then uninstalled Ruby and <a href="http://www.msys2.org/">MSYS2 64 toolkit</a> that ruby installed. Reinstalled version 2.4.3-1 (recommended). While installing MSYS2 toolkit it had a problem with Pacman installation but I installed the updated and it seemed to fix the problem. I also went off the OP student domain and used Eduroam but I am not sure this helped because it didn’t work on my home domain. I followed the step's again and to my surprise, the bundler worked and was able to create the site. 

Lesson learned: Read the instructions on the website before installing software. The newer releases of software are not always the solution.

