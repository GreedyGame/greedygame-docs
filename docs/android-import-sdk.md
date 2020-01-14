**Import GreedyGame Native Ads SDK**

Apps built with Android Studio can easily integrate with <a target="_blank" rel="noopener noreferrer" href="https://gradle.org">Gradle</a>.

Add the following to the app level `build.gradle`. (excerpt)

```gradle hl_lines="6"
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation 'com.android.support:appcompat-v7:26.1.0'
    ...............
    //greedygame sdk
    implementation 'com.greedygame:greedygame:8.8.16'
}
```

