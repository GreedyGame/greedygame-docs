#  **Import GreedyGame Native Ads SDK**

Apps build with XCode can easily import GreedyGame SDK with either <a target="_blank" rel="noopener noreferrer" href="https://cocoapods.org/">Cocoapod</a> or Manually.

**Cocoapod:**

If you are new to Cocoapod, Please check <a target="_blank" rel="noopener noreferrer" href="https://guides.cocoapods.org/using/getting-started.html">Cocoapod</a>

Once you created the podfile.Please open and add the below respective script according to your XCode version.


 If you are building with `XCode 10` or `XCode 10.1`

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
     pod ‘GreedyGameSDK’, ‘1.0.5’
  end
```

If you are building with `XCode 10.2`,`XCode 10.2.1` or `XCode 10.3`,

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
     pod ‘GreedyGameSDK’, ‘1.0.5.1’
  end
```

If you are building with `XCode 11` or `XCode 11.1`,

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
     pod ‘GreedyGameSDK’, ‘1.0.5.2’
  end
```

If you are building with `XCode 11.2`, `XCode 11.2.1` or `XCode 11.3`,

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
     pod ‘GreedyGameSDK’, ‘1.0.5.3’
  end
```

**Manual installation:**

For `XCode 10` or `XCode 10.1`,

 <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.5.zip" class="pure-material-button-contained">Download GreedyGame SDK For XCode 10 and 10.1</a>

For `XCode 10.2`, `XCode 10.2.1` and `XCode 10.3`,

  <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.5.1.zip" class="pure-material-button-contained">Download GreedyGame SDK For XCode 10.2, 10.2.1 and 10.3</a>

For `XCode 11` and `XCode 11.1`,

  <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.5.2.zip" class="pure-material-button-contained">Download GreedyGame SDK For XCode 11 and 11.1</a>

For `XCode 11.2`, `XCode 11.2.1` and `XCode 11.3`,

  <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.5.3.zip" class="pure-material-button-contained">Download GreedyGame SDK For XCode 11.2, 11.2.1 and 11.3</a>

 * Click `Source code (zip)` to download GreedyGame SDK.
 * Unzip and then add the `greedygame.framework`, `commons.framework` and `imageProcessing.framework` into your project.

*For Xcode series 10,*

   * Add these 3 frameworks under `Embedded Binaries` section in General or Build Phases

*For XCode series 11,*

   * Add these 3 frameworks under `Frameworks, Libraries and Embedded Content` section in General and set `Embed&Sign` like below

   <center><img src="/img/iOS/Embed-frameworks-XCode11.png" alt="" style="margin-left: 0px" width="500" height="150"></center>

!!! Check 
    <font size="2.5" color="OrangeRed">Please ensure that you have added the respective GreedyGame SDK according to the XCode version which you are going to use.</font>

