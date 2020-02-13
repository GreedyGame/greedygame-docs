
### **Importing GreedyGame Native Ads SDK**

Apps built with Xcode can easily integrate with <a target="_blank" rel="noopener noreferrer" href="https://cocoapods.org/">Cocoapods</a> or Manually.

**CocoaPod:**

To integrate GreedyGame SDK into your Xcode project using <a target="_blank" rel="noopener noreferrer" href="https://cocoapods.org/">Cocoapods</a>, specify it in your Podfile:

If you are building with `XCode 10` or `XCode 10.1`,

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
     pod ‘GreedyGameSDK’, ‘1.0.4’
  end
```

If you are building with `XCode 10.2`, `XCode 10.2.1`

```
  source 'https://github.com/GreedyGame/cocoapod-folio.git'   
  use_frameworks!

  target <Your Target Name> do
      pod ‘GreedyGameSDK’, ‘1.0.4.1’
  end
```
**Manual installation:**

If you are building with `XCode 10` or `XCode 10.1`,

 <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.4.zip" class="pure-material-button-contained">Download SDK For XCode 10 and 10.1</a>

If you are building with `XCode 10.2`, `XCode 10.2.1`

  <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin/archive/1.0.4.1.zip" class="pure-material-button-contained">Download SDK For XCode 10.2 and 10.2.1</a>

 * Unzip and then add the `greedygame.framework`, `commons.framework` and `imageProcessing.framework` into your project.
 * Add these 3 frameworks under `Embedded Binaries` section in General or Build Phases.