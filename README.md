AppleWatch Config steps (for Cordova CLI users):
================================================

DO NOT USE YET AS EVERYTHING IS IN ALPHA STATE AND WILL CHANGE!


####Prep:
  Install npm 'xcode' package because our hooks need it: `npm install -g xcode`

####CLI:
```
 cordova create applewatchtest
 cd applewatchtest
 cordova platform add ios
```

####XCode:
 File > New > Target > Apple Watch: Language ObjC, Select Glance and Notifications > Finish > Activate

####CLI:
```
 cordova plugin add ../../_Telerik_Verified_Plugins/AppleWatch
 cordova prepare
```

####XCode:
 Fix build target (8.2): Targets > WatchKit App > Deployment > iOS Deployment Target: iOS 8.2, see http://stackoverflow.com/questions/29242067/watchkit-apps-must-have-a-deployment-target-equal-to-ios-8-2-was-8-3

 Set CFBundleVersion (Bundle Version) and CFBundleShortVersionString (Bundle versions string, short) of all targets to the same value (use XCode's search feature and change all 3 .plist values


At this point your builds should succeed


####Finder:
 Overwrite the XCode WatchKit app .storyboard file with the one in this plugin

 If you want a quickstart, use `demo/index.html`


####XCode:
 App Groups: register an appgroup in your iOS member center (Identifiers > App Groups): group.<packagename> will do, like group.io.cordova.hellocordova, then add it to your App ID. Now generate a provisioning profile with the new App ID and add it XCode (download, then double-click the file should do it). In XCode, go to your targets and add this app group to both the phone and watch app targets (Capabilities tab)

  --> TODO figure out adding app group capability for Cordova app via plugin.xml? See old version of healthkit plugin.xml



####Tips:
 The simulator doesn't support local notifications

 Debugging of both the app and the extension: http://www.fiveminutewatchkit.com/blog/2015/3/13/how-to-debug-an-ios-app-while-the-associated-watchkit-app-is-running

 Notifications: http://natashatherobot.com/watchkit-actionable-notifications/