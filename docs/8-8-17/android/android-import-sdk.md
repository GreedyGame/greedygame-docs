**Import GreedyGame Native Ads SDK**

Apps built with Android Studio can easily integrate with <a target="_blank" rel="noopener noreferrer" href="https://gradle.org">Gradle</a>.

### Support Library Projects
If you using support libraries in your project, Add the following to the app level `build.gradle`. 

**`(excerpt)`**
```gradle hl_lines="6 8 9"
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation 'com.android.support:appcompat-v7:26.1.0'
    ...............
    //greedygame sdk
    implementation 'com.greedygame.legacy:greedygame:8.8.17'
    //Required Dependencies for GreedyGameSDK
    implementation 'com.android.support.constraint:constraint-layout:1.1.3'
    implementation 'com.android.support:palette-v7:28.0.0'

}
```

### Androidx Projects 
Since Greedygame SDK does not use AndroidX libraries yet, turn on jettifer by adding the following to `gradle.properties` file

**`(excerpt)`**
```gradle
...
android.enableJetifier=true
android.useAndroidX=true
...
```
Add the following to your app level `build.gradle`.

**`(excerpt)`**

```gradle hl_lines="6 8 9" 

dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation 'androidx.appcompat:appcompat:1.1.0
    implementation 'androidx.legacy:legacy-support-v4:1.0.0'
    //greedygame sdk
    implementation 'com.greedygame.legacy:greedygame:8.8.17'
    //Required Dependencies for GreedyGameSDK
    implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
    implementation 'androidx.palette:palette:1.0.0'
    ...
}

```
