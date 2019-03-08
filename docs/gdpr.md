

```
To enable GDPR privacy settings for GreedyGame's Native Android SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAds` insance before calling `load()`.

```Java tab=
// User has given a consent to protect their privacy
PrivacyOptions privacyOptions = new PrivacyOptions(true); // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions);
greedyGame.load();
```

```Java tab="Kotlin"
// User has given a consent to protect their privacy
val privacyOptions = PrivacyOptions(true) // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions)
greedyGame.load()
```

!!! note
    Load GreedyGameAds only after the user has given the consent. If `load()` is called before receiving the consent then the current app session will be considered as a consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.

# **iOS**
To enable GDPR privacy settings for GreedyGame's Native Android SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAds` instance before calling `load()`.

```Swift tab=
// User has given a consent to protect their privacy
let privacyOption = PrivacyOptions();
privacyOption.setNpa(npa: true) // By passing true means that the User has given consent to protect their privacy.
greedyGameAds.withPrivacyOptions(privacyOpt: privacyOption)

greedyGameAds.load()
```

```Objective-C tab="Objective-C"
 PrivacyOptions *privacyOption = [[PrivacyOptions alloc]init];
 [privacyOption setNpaWithNpa:YES]; // By passing YES means that the User has given consent to protect their privacy.
 [self.greedyGameAds setPrivacyOptionsWithPrivacyOpt:privacyOption];
    
 [self.greedyGameAds load];

 !!! note
    Load GreedyGameAds only after the user has given the consent. If `load()` is called before receiving the consent then the current app session will be considered as a consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.