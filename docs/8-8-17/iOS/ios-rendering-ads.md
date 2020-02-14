### ** Rendering Native Ads**

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

Once you get the `onAvailable(campaignId: String)` callback,publisher responsibility to get the native ad from the localpath with the ad unit and rendering it with your own UIImageView.

  * Create/add an `imageview` either programatically or using storyboard and set the `UserInteractionEnabled` property to `true`.
  * Add the tap gesture to the imageview to show interstitial.

**To fetch the Ad**

To fetch the Ad for a unit you need to call `getPath(unitId)` in `GreedyGameAgent` instance.

```Swift tab= 
//Create imageview in viewDidLoad method if you create an imageView programmatically.
let nativeAdImageView = UIImageView(frame: IMAGE_SIZE)

/*
Setting up Tap Gesture for the ad unit. 
This will launch an intersitial window when user clicks on the ad unit.
*/
let tapGesture = UITapGestureRecognizer(target: self, action: #selector(showUII(tapGesture:)))
nativeAdImageView.addGestureRecognizer(tapGesture)

/* tapGesture selector method.you can create your own method also*/
@objc func showUII(tapGesture:UITapGestureRecognizer){
    greedyGameAgent?.showUII(unitId: "FLOAT_ADUNIT_CREATED")
}

/*call this method when you get the onAvailable callback method*/
func loadAd(){
	if let path = greedyGameAgent?.getPath(unitId: ADUNIT_CREATED) { 
		// GreedyGameAgent has an ad that can be rendered for this Unit id. 
		nativeAdImageView.image = UIImage(contentsOfFile: path)
		nativeAdImageView.isUserInteractionEnabled = true 
	} else {
		// GreedyGame does not have a valid Ad for this Unit id at the moment
		nativeAdImageView.image = UIImage(named: "Default_Image_Name")
		nativeAdImageView.isUserInteractionEnabled = false 
	}
}
```

```Objective-C tab="Objective-c"
//Create imageview in viewDidLoad method if you create an imageView programmatically.
UIImageView *nativeAdImageView = [[UIImageView alloc]initWithFrame: IMAGE_SIZE]; 

/*
Setting up Tap Gesture for the ad unit. 
This will launch an intersitial window when user clicks on the ad unit.
*/
UITapGestureRecognizer *tapGesture = [[UITapGestureRecognizer alloc]initWithTarget:self action:@selector(showUII:)];
[nativeAdImageView addGestureRecognizer:tapGesture];

/* tapGesture selector method.you can create your own method also*/
-(void)showUII:(UITapGestureRecognizer*)tapGesture{
   [greedyGameAgent showUIIWithUnitId:@"FLOAT_ADUNIT_CREATED"];
}

/*call this method when you get the onAvailable callback method*/
-(void)loadAd{
	NSString *path = [greedyGameAgent getPathWithUnitId:ADUNIT_CREATED];
	    
	if (path.length != 0){
		// GreedyGameAgent has an ad that can be rendered for this Unit id. 
	    nativeAdImageView.image = [UIImage imageWithContentsOfFile:path];
	    nativeAdImageView.userInteractionEnabled = YES;
	}else{
		// GreedyGame does not have a valid Ad for this Unit id at the moment
	    nativeAdImageView.image = [UIImage imageNamed:@"Default_Image_Name"];
		nativeAdImageView.userInteractionEnabled = NO;
	}
}
```

**NOTE:** Ensure that you mention the correct Unit ID in the highlighted line.

!!! warning
    
    It's the publisher responsibility to call `getPath(unitId)` at relevant places to render the ads. For example, in `onAvailable()` callback of the `CampaignStateListener` or when you are changing the `ViewController`, calling `getPath(unitId)` at the start of the ViewController will help you display the ad correctly


**NOTE:** When the Campaign state is `onUnavailable()` or `onError(error)`, ensure that you replace the ad unit by the default texture of your app.
