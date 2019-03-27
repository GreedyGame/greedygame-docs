### **I unable to see ads in my app. How do I troubleshoot?**
This question deals with Android troubleshooting. For Unity, Cocos, iOS platforms, please visit their respective pages

1. Check Android Logs to see relevant information on misconfiguration. All GreedyGame logs start with a 'GG' prefix
2. Check your internet connection and disable proxies, if any  
3. Check if the [GreedyGame Activity](/android/#update-your-androidmanifestxml) is present in the manifest file  
4. Did the [GreedyGame Panel App](https://play.google.com/store/apps/details?id=com.greedygame.androididfinder) throw an error message? Follow the steps in the app for troubleshooting
5. Make sure that you have correctly configured the [Game Id](/android/#creating-game-id) and the [Ad Unit(s)](/android/#creating-ad-units) as a part of the integration steps

If you are still unable to see ads, then send out an emails to <Insert Support Email here> stating your problem.

### **I can see some ads but not all of them. What could be the problem?**
If you are able to see some ads in the Game, then the basic integration is working fine. A general cause of this behaviour is when developers accidentally forget to add the relevant Ad Unit Id in the Ad Request Builder call. Please check [this](/android-advanced/#initializing-greedygameads) section for more information

### **Why do I need Google PlayServices to be integrated? Which is the minimum supported version?**
In order to comply with Google's Advertising Guidelines, there are certain dependencies on Google Play Services. Also, Google AdMob launched a complete Native Advanced Ad support from version 11.0.4 and hence that is the minimum required supported version

### **Which Activities do I need to declare as a part of my manifest?**
You need to include a GreedyGame activity for completing the integration process. The same is mentioned in the integration step [here](/android/#update-your-androidmanifestxml). Do not forget to change the orientation to match your app's orientation. 
```xml hl_lines="6"
<activity
    android:name="com.greedygame.android.core.campaign.uii.GreedyGameActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="portrait"
    android:theme="@style/Theme.GGTransparent">
</activity>
```

### **What should I keep in mind while creating Ad Units?**
GreedyGame provides you with flexibility to create Ad Experiences that are tailor made for your game. As a Developer, you have the freedom of creating units of multiple sizes depending on the Activity or Game Scene design. We do have the following guidelines in place:  

1. Try to keep the number of units in a game below 10  
2. Find natural fitting spots for your units which do not hamper the user experience  
3. Keep the sizes of a unit below 500px in a single dimension  
4. Integrate the maximum number of spots available in a game for monetization. You can always enable or disable a unit from our dashboard after integration  

### **What happens when I turn off Ad Unit clickability?**
Ad Unit performance has direct co-relation to the revenue being generated. Ad Campaigns can be run by Advertisers in different modes but CPM(Cost Per Mille) and CPC(Cost Per Click) are the most common. If clickability is turned off, your Ad Unit will still be monetized on the CPM campaigns but will stop generating revenues from CPC ones. This may result in a loss in revenue. We recommend fine tuning this setting only when you have had enough data on the Ad Unit performance to make viable recommendations


### **Why can't I set the height and width attributes to wrap_content?**
