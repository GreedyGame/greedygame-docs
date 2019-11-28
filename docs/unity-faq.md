
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


### **Where to find the Android manifest file??**
Once you build the Unity project for Android(even a blank project) then go to **"&lt;ProjectName&gt;\Temp\StagingArea\"**  copy the Android manifest file and import the Android Manifest file to the following location **"Assets/Plugins/Android/AndroidManifest.xml"** .
Then make the Android manifest changes you want to make.
<br/>
To know more about Unity generation of Android manifest file and how it uses.<a target="_blank" rel="noopener noreferrer" href="https://docs.unity3d.com/Manual/android-manifest.html">here</a>.
<br/>
To know more about Android manifest file <a target="_blank" rel="noopener noreferrer" href="https://developer.android.com/guide/topics/manifest/manifest-intro.html">here</a>.


