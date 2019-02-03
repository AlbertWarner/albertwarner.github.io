---
layout: post
title: Problems with Production Server
date: 2018-09-09 15:00 +1200
---
When we merge to the master branch on gitlab, it pushes to web server container, this makes the website live. This can be noted as our production server and the client can use it to demo the work and test the website. We seem to be having issues with the website running on the production server, the reason for this is, our development server Kate could be set up with a lot fewer rules and it is showing the work done without any error but on the production that is not the case. The meaning of this is, we must validate each page and see where our problems are and hopefully don’t need to make too many changes.
