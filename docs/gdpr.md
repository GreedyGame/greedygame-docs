### **Android**

To enable GDPR privacy settings for GreedyGame's Native Android SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAgent` instance before calling `init()`.

```Java tab=
// Before calling init from the GreedyGameAgent instance you have to set the NPA.
PrivacyOptions privacyOptions = new PrivacyOptions();
privacyOptions.setGgNpa(true);
agent.withPrivacyOptions(privacyOptions);
agent.init();
```

<!-- 
```Java tab="Kotlin-Beta" hl_lines="3"
// User has given a consent to protect their privacy
val privacyOptions = PrivacyOptions(true) // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions)
greedyGame.load()
```
 -->
!!! warning
    Initialise GreedyGameAgent only after the user has given the consent. If `init()` is called before receiving the consent then the current app session will be considered as a consent of using privacy information. 

    AdMob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.

### **iOS**
To enable GDPR privacy settings for GreedyGame's Native iOS SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAgent` instance before calling `initialize()`.

```Swift tab=
let privacyOptions = PrivacyOptions()
privacyOptions.setNpa(npa: true)
greedyGameAgent?.setPrivacyOptions(privacyOpt: privacyOptions)
greedyGameAgent.initialize()
```

```Objective-C tab="Objective-C"
PrivacyOptions *privateOptions = [[PrivacyOptions alloc]init];
[privateOptions setNpaWithNpa:YES];
[self.greedyGameAgent setPrivacyOptionsWithPrivacyOpt:privateOptions];
[self.greedyGameAgent initialize];
```

!!! warning
    Load GreedyGameAgent only after the user has given the consent. If `load()` is called before receiving the consent then the current app session will be considered with the consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.