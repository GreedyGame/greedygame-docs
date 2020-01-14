
## Best Practices For Games

### ** 1. Where should I add units in my app?**

   Priority to add ad units in various game screens should be in the following order

``Main Menu → Gameplay →  Exit Screen → Other Screens.`` 

<center><img src="/img/new/game-units.png" alt="" style="margin-left: 0px" width="400" height="600"></center>


### ** 2. Does the position of the ad-unit matter on the screen? **
 
   The positioning of the ad unit also impacts the CPMs. The ad unit should be placed in closer proximity to action buttons 	within the game if clickable and within the central cross-axis of the game if non-clickable in the property.

`Example:` 

   placing the button as another tile in a menu screen. Ads that blend in more naturally within the game UI are more likely to be clicked by the users.


 <center><img src="/img/new/ad_unit_position.png" alt="" style="margin-left: 0px" width="400" height="200"></center>


!!! note
     Please check GreedyGame best Native Ad placements <a target="_blank" rel="noopener noreferrer" href=" https://greedygame.com/native-ad-examples-gallery/">here</a>


### ** 3. How many ad units should I add? **

   We recommend adding a minimum of 2 and a maximum of 10 units within any game. Using more than 10 units in games results in performance issues as GreedyGame SDK downloads assets for all units every time an ad refresh is called.

 <center><img src="/img/new/mutiple_Ads.png" alt="" style="margin-left: 0px" width="400" height="200"></center>


### ** 4. What can be the maximum unit dimensions? **

   Unit sizes should fit the size of your app’s HUD.Ideally,units should not be more than 1000x1000 pixel. (Minimum size - 100x100 px)

### ** 5. What do I need to keep in mind when creating an ad-unit? **

   Please create a square/rectangle transparent texture. While setting the unit up, do let us know the exact position and size on the screen where you want the ad to show. This helps us debug the units.



### ** 6. Do I need to create the ad-template of the ad-unit? **

   No, do not provide the ad-template. Only create a square/rectangle transparent texture. The JSON (frame) of the ad-template is created dynamically. The assets for the ad-template are downloaded when an ad refresh is called. The ad-template is optimized and updated by our team basis the data collected to improve click-through-rates. A transparent texture helps us change the ad-template on the fly. If you provide an ad-template, we’d require to update the SDK every time any unit optimization needs to be done

### ** 7. Can I create units that are non-clickable and show ads on them? **
   
   Yes, you can but currently, the fill for it individually is very low. We’d recommend a small clickable unit be used in conjugation with it. This way, we can show multiple elements of the same ad across a set of units (clickable and a non-clickable) thus increasing the Click-through-rates on the ad impression.

## Do’s and Don’ts
 
** Unit too small **

 <center><img src="/img/new/small_unit.png" alt="" style="margin-left: 0px" width="400" height="200"></center>

 <center><img src="/img/new/large_unit.png" alt="" style="margin-left: 0px" width="400" height="200"></center>


** Units should not cover game elements/ each other **


 <center><img src="/img/new/overlapping.png" alt="" style="margin-left: 0px" width="400" height="200"></center>


 <center><img src="/img/new/no_overlap.png" alt="" style="margin-left: 0px" width="400" height="200"></center>


**Here are some inspirations for native ad placements on our <a target="_blank" rel="noopener noreferrer" href="https://greedygame.com/native-ad-examples-gallery/">Native Ad Gallery</a>**
