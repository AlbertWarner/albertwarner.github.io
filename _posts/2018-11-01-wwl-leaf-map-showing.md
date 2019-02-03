---
layout: post
title: WWL Leaf map showing
date: 2018-11-01 21:09 +1300
---

Another fun day for learning something new. We need to show on a map with indications of where the user walked on a google maps. I went searching for some javascript or how to imply what I want on google maps, my searches were coming up with some hard work. Then Alex came to talk to me and we got chatting about what I was looking for and he said I must use <a href= "https://leafletjs.com/examples/quick-start/"> Leaflet </a> Wow was this an amazing site and so well documented, I love this.

I followed the guide and did some modifications to the sit and got it to the map to show. I showed Adon and he seemed impressed. We started playing with the coordinates to see how they worked. Should be a simple for loop running through the data from the DB and displaying it.

<h3>Ajax Uploading Files </h3>
```php
  <div id="mapid"  style="height:470px;"></div>
                   <script>
                    var mymap = L.map('mapid').setView([-45.865843, 170.519456], 13);

                   var marker = L.marker([-45.865843, 170.519456]).addTo(mymap);
                   var marker = L.marker([-45.865843, 170.519556]).addTo(mymap);
                   var marker = L.marker([-45.865843, 170.519656]).addTo(mymap);

                    L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw', {
                      maxZoom: 18,
                      attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, ' +
                        '<a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
                        'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
                      id: 'mapbox.streets'
                    }).addTo(mymap);

                    marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();

                 </script>
```
![alt text](/assets/images/Project2/map.PNG " map ")

Image 1. Leaflet Map implemented by Django

<h3>Reflection </h3>

I learned a lot from the leaflet page and how to use their maps is well documented and it was fun to see it work with Django. Very nice learning curve and lots of fun.