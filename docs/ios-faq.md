`
dyld: Library not loaded: @rpath/commons.framework/commons 
Referenced from: <Your  app path> 
Reason: image not found 
`

**Answer:**</br>
  Add Commons.framework Under `Embedded Binaries` section in General/Build Phases.

`
dyld: Library not loaded: @rpath/imageProcessing.framework/commons
Referenced from: <Your  app path>
Reason: image not found
`

**Answer:**</br>
  Add imageProcessing.framework Under `Embedded Binaries` section in General/Build Phases.

`
dyld: Library not loaded: @rpath/greedygame.framework/commons
Referenced from: <Your  app path>
Reason: image not found
`

**Answer:**</br>
  Add greedygame.framework Under `Embedded Binaries` section in General/Build Phases.

`dyld: Library not loaded: @rpath/libswift_stdlib_core.dylib
  Referenced from: <Your app path>
  Reason: image not found
  `

**Answer:**</br>
  	Go to `Build setting` and make `Always Embed Swift Standard Libraries` to `YES`