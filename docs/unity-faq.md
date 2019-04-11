
### **Which versions of Unity do you support?**
GreedyGame's SDK can be integrated in Unity Versions 5.3 and above. However, the <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/unity-plugin/releases/">Unity Plugin</a> is supported from Unity 2017 and above.

### **How can I use code stripping?**
Currently, you cannot use the Unity SDK with code stripping enabled. This support will be introduced in the future versions

### **Why are my test ads different from what was shared in the mocks?**
While we try and ensure the same experience as depicted in mocks, sometimes production ads might contain elements which may behave differently. Reach out to your Account Manager to ensure a smooth experience.


### **How do I set up COPPA flag for indicating an app directed towards children?**
The GGConfig object that you pass during initialization contains an API for setting COPPA.
```
GGConfig config = new GGConfig();
config.EnableCoppa (true);
```

### **How do I pass relevant GDPR information to GreedyGame's SDK?**
The GGConfig object that you pass during initialization contains an API for setting Non personalized ads to conform to GDPR. So if you detect a user who hasn't given consent then during initialization of the SDK you should pass config after setting the NPA flag. Setting it to true will serve non-personalized ads only.
```
GGConfig config = new GGConfig();
config.EnableNpa (true);
```

