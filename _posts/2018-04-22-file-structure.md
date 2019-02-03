---
layout: post
title: File Structure
date: 2018-04-22 21:02 +1200
---

What have I done?

This was an interesting change about to happen. I thought we were being punished, taking 10 steps backward because everything was going to change, and nothing was going to work, just as it seemed we were getting everything moving forward and starting to work but I was very wrong. This move would be better in so many ways, I wish we had done this type file structure and design from the beginning, it would’ve made the workload 10 times easier. As they say, we learn from our mistakes and have good people to help correct us.

This adventure started when I asked Adon to explain the new change he wanted to be implemented. This change is to have one PHP file build the aircraft or helicopter forms. As shown in figure 1, Adon gave us 2 choices. We selected option number 2, which was single PHP file that would build an HTML file by including the header and the footer and all other required information.

![alt text](/assets/maindoc.JPG " choices ")

Figure 1. Adon gave us options to move forward.

That was only the beginning of the massive changes to happen. Adon explained that a new server would be created by the Operations team and when we push to the master branch on Gitlab it would push directly to the new server and be published live. Meaning the master branch on Gitlab would be our working branch. I created a development branch which would act as the master branch, the team could push or pull from their branches to the development branch. When everyone is happy with the website to go live it could be pushed from the development to the master branch.

![alt text](/assets/gitlab.JPG " choices ")

Figure 2. Gitlab development branch created

The Second big change to happen was to the file structure. All the files were in the main directory called ACL, the only directory that was different was the model's directory which was called by the controllers to push data to the database. This structure needed to completely change, one of the reasons was, the website was going to have smaller sections, for example, the header.php and having all these small files in one directory would become confusing. With a better file structure, the developer can go look for a file in a specific directory and find what he is looking for. The second reason is that it is standard practice to have files in subdirectories and it looks neater and more structured.

![alt text](/assets/oldfile.JPG " old file structure ")
 
Figure 3. Old File structure

The change of the file structure would be easy, I thought "hey an easy task to do", but in the back of my mind, I was thinking when these files need to talk to each other it would be a major problem. I thought I would be seeing error after error, the ‘error nightmare’ it would be called.

![alt text](/assets/newfile.JPG " new file structure ")

Fig 4. The new file Structure

Does that not look so much better? The assets directory would hold the CSS and IMG subdirectories and the views directory would hold the forms and the reports subdirectories.

I felt this was neat and looked like a conventional website, but it would change again.


Fig 5 shows the plan of how the main.php would be built and how it would function

![alt text](/assets/mainplan.JPG " main plan ")

Fig 5. main.php planning 

The aircraft is a form I have been working on since the beginning of the semester, so I decided I would break that one first and try to get everything to work. I removed the header and created a new file called head.php and I stored that file in the common directory and I did the same for the footer, also in the footer file I closed the body and HTML tags. All that was left inside the aircraft.php was the raw information of the website, contact details, insurance details etc.

The main.php would build up the page, by including the subsections to create the website. Fig 6 shows how the main works.

![alt text](/assets/mainsetup.JPG " main setup ")

Fig 6. main.php  

At the bottom of the controller, there would be a variable called $page and it would have the webpage name stored in that variable. This variable would be included on the main.php as shown in Fig 6 and this would call the section required between the header and footer of the website. In theory, the page is built up by 3 different files, but it still looks and works like a normal page.

The aircraft page was split up even further. Each section under its own heading was moved into its own PHP file. For example, the heading called contact details and all the information below that heading was moved to a file called contact.php which was stored in the components directory. The reason for this is, later when we introduce users and what the users can see, if a user is not allowed to see the insurance details then that file will not be included. The other reason is to stop repeating ourselves and if we did this from the beginning, life would have been so much easier. Where it becomes easy is, if all 8 pages need a contact details section, then all 8 pages include one contact.php and this makes it less work. As they say work smarter, not harder.   

![alt text](/assets/subfiles.JPG " subfiles ")

Figure 7 Show the aircraft.php and it is including all the sub files.   

In conclusion, this website is starting to look smarter and the changes look so much better and easier than first thought. The website is functioning exactly as it was before but with a new file structure, yes there will be a few more changes to get all the files talking but all is good for now.          

What are my Obstacles?  

While testing the above webpage to see if everything was working, I ran into a problem. 

![alt text](/assets/problem.JPG " problem ")

Fig8. The problem while testing

The problem is the controller is in the controller directory, but it was looking for main.php in the same directory. The main.php file is in the root directory, so the aircraft controller file had to move up one directory into the root and find the file called main. When searching the problem many people said to move up one directory in PHP use “../ ”  Fig 8 you can see that was what I used to include the page but it did not work.

Solution to my problem was found in the <a href="http://php.net/manual/en/function.dirname.php "> PHP manuel</a>, fig 9 show where I found the solution.

![alt text](/assets/fix.JPG " fix ")

Figure 9. Solution to the directory problem

The new file structure had to be pushed to Gitlab and moved to the development branch so that the rest of the team could carry on working on the website and make the required changes to the other pages. First, I feel Gitlab is not always happy with the changes, it seemed to work against me. I pushed up the new file structure and git accepted it but kept the old files but at the same time adding the new ones, so I had to manually remove the old files and submit every change, till my Gitlab branch looked the same as my new directory. Then I had to merge the directory to the development branch and again I had to manually remove the unwanted files. 

Finally made all the necessary changes to my directory and then had to merge them again with the development branch, I got merge errors and had to open the directory with visual code and accept all the new changes. With the master, it seemed to accept the changes but with the development branch, we might have a few merge errors in future.

![alt text](/assets/git.JPG " git ")

Figure 10. Gitlab and how I had to fix the merge errors

What do I want to achieve? 

Hope the file structure is correct and now start on the hashing of the form ID, which I was supposed to do 2 weeks ago.

