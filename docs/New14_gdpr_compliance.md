## **Compliance with GDPR**

**This is not mandatory, but only if your app has to be GDPR Compliant**

!!! note
    **<a target="_blank" rel="noopener noreferrer" href="https://greedygame.com/post/gdpr">Know More About GDPR</a>**

To enable GDPR privacy settings for GreedyGame's Native Android SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAgent` insance before calling `init()`.

```Java tab=
// Before calling init from the GreedyGameAgent instance you have to set the NPA.
PrivacyOptions privacyOptions = new PrivacyOptions();
privacyOptions.setGgNpa(true);
greedyGameAgent.withPrivacyOptions(privacyOptions);
greedyGameAgent.init();
```

<!-- ```Java tab="Kotlin"
// User has given a consent to protect their privacy
val privacyOptions = PrivacyOptions(true) // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions)
greedyGame.load()
```
 -->
!!! note
    Load GreedyGameAgent only after the user has given the consent. If `init()` is called before receiving the consent then the current app session will be considered as a consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.

