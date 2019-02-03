---
layout: post
title: Maintenance User Fixing Errors
date: 2018-09-17 18:43 +1200
---

The maintenance section problem I have known about for a while, it would push to the DB when the submit button was hit but there are sections that the maintenance person can see, and these sections are just removed. The problem is when the user submits the form, the data is posted to the controller but the fields that aren’t included can not post anything to the controller and you get the errors like in Image 1. 

<img src="{{ 'assets/images/Project2/mainterror.JPG' | relative_url }}" alt="errors" />

Image 1. Aircraft maintenance form submitted

Solution to the above error, I did some googling and found <a href="https://stackoverflow.com/questions/1992114/how-do-you-create-a-hidden-div-that-doesnt-create-a-line-break-or-horizontal-sp"> how to create hidden div on stack overflow</a>. It worked amazing quick fix, so the information will be hidden from the user and all the information will post like normal.

 <h3>Solution to the maintenance error</h3>
 
{% highlight php %}
<div style="display:none">
        <!--Insurance Details Section!-->
        <?php include_once ($formComponentUrl. 'insuranceDetails.php');?>
        </div>
        <!--Aircraft Details!-->
        <h2 class="text-center">Aircraft Details</h2>
        <?php include_once ($formComponentUrl . 'aircraftDetails.php');?>

{% endhighlight %}
