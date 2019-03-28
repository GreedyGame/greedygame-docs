
### **What is the minimum supported Xcode version?**
The minimum supported version is Xcode-10

### **What is the size of the iOS SDK?**
The size of the iOS SDK is ~57MB

### **What is the minimum swift version?**
We support Swift-4 and above

### **My app is crashing with `Library not loaded` error. What am I doing wrong?**
You need to embed the GreedyGame SDK not just link it to compile your code. The following table maps the most common missed framework scenarios. These frameworks need to be added in the `Embedded Binaries` section in the General/Build phases.

| Error                                    | Resolution                     |
| ---------------------------------------- | ------------------------------- |
| @rpath/commons.framework/commons         | Add `Commons.framework`         | 
| @rpath/imageProcessing.framework/commons | Add `imageProcessing.framework` |
| @rpath/greedygame.framework/commons      | Add `greedygame.framework`      |
| @rpath/libswift_stdlib_core.dylib        | Go to `Build setting` and set `Always Embed Swift Standard Libraries` to `YES` |
