## **Compliance with GDPR**

**This is not mandatory, but only if your app has to be GDPR Compliant**

!!! note
    **<a target="_blank" rel="noopener noreferrer" href="https://greedygame.com/post/gdpr">Know More About GDPR</a>**

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

!!! note
    Load GreedyGameAgent only after the user has given the consent. If `initialize()` is called before receiving the consent then the current app session will be considered with the consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.