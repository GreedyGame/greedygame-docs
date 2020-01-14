You can create a **ImageView**, where you want the ad to be rendered.

**For example, if an ad needs to be shown at the spot in the red box**

<img src="/img/new/11a_mock.jpg" alt="" style="margin-left: 50px" width="500" height="280">

**Create an ImageView of the size where the ad needs to be rendered**

<img src="/img/new/11b_mock.jpg" alt="" style="margin-left: 50px" width="500" height="280">

**On this ImageView, assign the rendering script, to render the ad.**

Please note that the final design of the ad unit template will be done by the GreedyGame engine.

<img src="/img/new/11c_mock.jpg" alt="" style="margin-left: 50px" width="500" height="280">


**GreedyGame engine also keeps on optimizing the native ad unit design to improve CTR.**

<img src="/img/new/11d_mock.jpg" alt="" style="margin-left: 50px" width="500" height="280">


!!! note
    More information about unit design can be found under **<a target="_blank" rel="noopener noreferrer" href="/best-practices">Best Practices</a>** section.


### **Implementation of Rendering Code**
Implement the following custom rendering code to render Native Ads in your `ImageView`.

Follow the example to do the same.

**To fetch the Ad**

To fetch the Ad for a unit you need to call `getPath(unitId)` in `GreedyGameAgent` instance.

```Java tab= hl_lines="2"

void loadAd(){
    String unitId = "YOUR FLOAT UNIT HERE";
    ImageView iv = (ImageView) findViewById(R.id.your_imageview_id);
    /*
    Setting up click listener for the ad unit. 
    This will launch an intersitial window when user clicks on the ad unit.
    */
    View.OnClickListener unitClick = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            greedyGameAgent.showUII(unitId); 
        }
    };

    boolean bitmapChanged = false;
    String path = greedyGameAgent.getPath(unitId);
    if (path != null) {
    File file = new File(path);
    if (file.exists()) {
        Bitmap bm = BitmapFactory.decodeFile(file.getAbsolutePath());
        if (bm != null) {
            // Use it on your element which needs to be branded.
            bitmapChanged = true;
            iv.setImageBitmap(bm); // This is where you actually set the Native Ad
            iv.setOnClickListener(unitClick);
        }
    }
    }

    if(!bitmapChanged) {
    // Change the asset to original or default texture
    iv.setImageBitmap(originalBitmap);
    iv.setOnClickListener(null);
    }
}
```

**NOTE:** Ensure that you mention the correct Unit ID in the highlighted line.

<!-- ```Java tab="Kotlin"
val adUnitIV = ImageView(context) // AdUnit ImageView to render ad
// Game logics
val unitPath = greedyGame.getPath(ADUNIT_CREATED)
if(unitPath.isNotEmpty()) {
    // GreedyGameAgent has an ad that can be rendered for this Unit id.
    val adBitmap = BitmapHelper.getBitmap(unitPath)
    adUnitIV.bitmap = adBitmap
} else {
    // GreedyGame does not have a valid Ad for this Unit id at the moment
}
``` -->

!!! warning
    
    It's the publisher responsibility to call `getPath(unitId)` at relevant places to render the ads. For example, in `onAvailable()` callback of the `CampaignStateListener` or when you are changing the `Activity`, calling `getPath(unitId)` at the start of the activity will help you display the ad correctly


**NOTE:** When the Campaign state is `onUnavailable()` or `onError(error)`, ensure that you replace the ad unit by the default texture of your app.
