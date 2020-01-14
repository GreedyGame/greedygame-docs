
## Best Practices For Apps

### ** 1. Where should I add units in my app? **
  
 Priority to add ad units in various App screens should be in the following order
 Carousel, Menu wall, In-feed, Exit Screen, App Overlays, Pop-ups

  <center><img src="/img/new/in_App.png" alt="" style="margin-left: 0px" width="700" height="280"></center>


### ** 2. Does the position of the ad-unit matter on the screen? **

The positioning of the ad unit also impacts the CPMs. The ad unit should be placed in the 2nd or 3rd position on the Menu Wall, In-Feed or Carousel.

  <center><img src="/img/new/in_app_units.png" alt="" style="margin-left: 0px" width="450" height="280" class="center"></center>


!!! note
     Please check GreedyGame best Native Ad placements <a target="_blank" rel="noopener noreferrer" href=" https://greedygame.com/native-ad-examples-gallery/">here</a>

### ** 3. How many ad units should I add? **
 
We recommend adding a minimum of 2 and a maximum of 10 units within any game. Using more than 10 units in Applications results in performance issues as GreedyGame SDK downloads assets for all units every time an ad refresh is called.

  <center><img src="/img/new/appBrowzer_main_screen.jpg" alt="" style="margin-left: 0px" width="250" height="450"></center>


### ** 4. What can be the maximum unit dimensions? **

Unit sizes should fit the size of your app’s HUD.Ideally,units should not be more than 1000 x 1000 pixel.
(Minimum size - 100 x 100 px).

### ** 5. What do I need to keep in mind when creating an ad-unit? **

Please create a square/rectangle transparent ImageView. While setting the unit up, do let us know the exact position and size on the screen where you want the ad to show. This helps us debug the units.

 <center><img src="/img/new/android_studio.png" alt="" style="margin-left: 0px" width="600" height="400"></center>


### ** 6. Do I need to create the frame of the ad-unit? **

No, do not provide an ad-template. Only create a square/rectangle transparent ImageView. The JSON (frame) for the ad-template is created dynamically. The assets for the ad-template are downloaded when an ad refresh is called. The ad-template is optimized and updated by our team basis the data collected to improve click-through-rates. A transparent unit helps us change the ad-template on the fly. If you provide an ad-template, we’d require to update the SDK every time any unit optimization needs to be done.



### ** 7. Can I create units that are non-clickable and show ads on them? **

For apps, we do not recommend putting non-clickable units as most elements of the apps are clickable and the user expects a response on click on these elements. The introduction of the non-clickable unit might give an impression to the users off a faulty application.

## Do’s and Don’ts

** Unit too small **

<center><img src="/img/new/App_small_nit copy.png" alt="" style="margin-left: 0px" width="250" height="450"></center>

<center><img src="/img/new/App_large_unit copy.png" alt="" style="margin-left: 0px" width="250" height="450"></center>


** Units should not cover game elements/each other **

<center><img src="/img/new/app_ad_unit_overlap.png" alt="" style="margin-left: 0px" width="250" height="450;align:left"></center>

<center><img src="/img/new/app_ad_unit_no_overlap.png" alt="" style="margin-left: 0px" width="250" height="450;align:right"></center>



** Ad size should match other elements **

  <center><img src="/img/new/appBrowzer_main_screen.jpg" alt="" style="margin-left: 0px" width="250" height="450"></center>


**Here are some inspirations for native ad placements on our <a target="_blank" rel="noopener noreferrer" href="https://greedygame.com/native-ad-examples-gallery/">Native Ad Gallery</a>**

