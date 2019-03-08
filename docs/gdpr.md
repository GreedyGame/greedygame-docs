
# **iOS**
# **Compliance with GDPR**
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
```