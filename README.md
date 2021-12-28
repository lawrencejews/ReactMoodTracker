# MoodTracker
##### Course website: [MoodTracker](https://kadikraman.github.io/react-native-beyond-basics/)
- Run to start metro server -> `npx react-native start`
- Open android studio then build within the android folder -> `npx react-native run android or yarn android`
#### Navigation
- Using react navigation library: 
```
yarn add @react-navigation/native react-native-screens react-native-safe-area-context @react-navigation/bottom-tabs 
# or
npm install @react-navigation/native react-native-screens react-native-safe-area-context @react-navigation/bottom-tabs
```
- Add this piece for Android development in the ` MainActivity.java `file `android/app/src/main/java/moodtracker/MainActivity.java`: 
``` 
@Override
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(null);
} 
```
- then Add this import to the top of the same file: `import android.os.Bundle;`
- Remember that turning ` "skipLibCheck": true `in tsconfig only run on the code written.
#### Local Storage 
- For Async storage locally: 
```
yarn add @react-native-async-storage/async-storage
# or
npm install @react-native-async-storage/async-storage
```
#### Vector-Icon and Image
- For image rendering in production: [react-native-fast-image](https://github.com/DylanVann/react-native-fast-image)
- For vector-icons: i.e svg rendering[react-native-svg](https://github.com/react-native-svg/react-native-svg)
```
yarn add react-native-svg
# or
npm install react-native-svg
 ```
 - To clean your `.svg` use [react-svgr](https://react-svgr.com/playground/)
 #### Fonts, Animation and Icon
 - Create a root file for fonts to be used Globally: `react-native-config.js`
 ```
 module.exports = {
  assets: ['./assets/fonts'],
};
```
- Then run in the terminal `npx react-native link`
- LayoutAnimation is enable by default on `ios` but experiemental on Android: Add code below to `App.tsx`
```
import { Platform, UIManager } from 'react-native';

if (Platform.OS === 'android') {
  if (UIManager.setLayoutAnimationEnabledExperimental) {
    UIManager.setLayoutAnimationEnabledExperimental(true);
  }
}
```
- Reanimated library for React-Native built to address performance issues
- Note react should be `react-native@0.66.4` for Reanimated to work
```
yarn add react-native-reanimated@2.3.0-alpha.2
# or
npm install yarn add react-native-reanimated@2.3.0-alpha.2
```
- You have to create a babel plugin
```
module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
+  plugins: ['react-native-reanimated/plugin'],
};
```
- Then enable `Hermes engine` build time for Android `android/app/build.gradle` 
```
project.ext.react = [
  enableHermes: true // <- here | clean and rebuild if changing
]
```
- and plug Reanimated in `MainApplication.java`
``` 
import com.facebook.react.bridge.JSIModulePackage; // <- add
import com.swmansion.reanimated.ReanimatedJSIModulePackage; // <- add
...
private final ReactNativeHost mReactNativeHost = new ReactNativeHost(this) {
...

    @Override
    protected String getJSMainModuleName() {
      return "index";
    }

    @Override
    protected JSIModulePackage getJSIModulePackage() {
      return new ReanimatedJSIModulePackage(); // <- add
    }
  };
```
- Animation combined with gesture events
```
yarn add react-native-gesture-handler
# or
npm install --save react-native-gesture-handler
```
- Update your `MainActivity.java` but don't forget to add an import of the library to `index.js`
```
package com.swmansion.gesturehandler.react.example;

import com.facebook.react.ReactActivity;
+ import com.facebook.react.ReactActivityDelegate;
+ import com.facebook.react.ReactRootView;
+ import com.swmansion.gesturehandler.react.RNGestureHandlerEnabledRootView;
public class MainActivity extends ReactActivity {

  @Override
  protected String getMainComponentName() {
    return "MoodTracker";
  }
+  @Override
+  protected ReactActivityDelegate createReactActivityDelegate() {
+    return new ReactActivityDelegate(this, getMainComponentName()) {
+      @Override
+      protected ReactRootView createRootView() {
+       return new RNGestureHandlerEnabledRootView(MainActivity.this);
+      }
+    };
+  }
}
```
#### App Icons
App Icon to prevent flash when loading page on mobile.[react-native-splash-screen](https://github.com/crazycodeboy/react-native-splash-screen)
```
yarn add react-native-splash-screen
# or
npm install react-native-splash-screen
```
- then link it `npx react-native link react-native-splash-screen`
- Add this code to `AppDelegate.m` after  `cd ios && pod install`
```
#import "AppDelegate.h"

#import <React/RCTBundleURLProvider.h>
#import <React/RCTRootView.h>
+#import "RNSplashScreen.h"

@implementation AppDelegate

 (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    // ...other code

+    [RNSplashScreen show];

    return YES;
}

@end
```
- For Android: update `MainActivity.java` to use `react-native-splash-screen`
```
+import android.os.Bundle;
+import org.devio.rn.splashscreen.SplashScreen;

public class MainActivity extends ReactActivity {
   @Override
    protected void onCreate(Bundle savedInstanceState) {
+        SplashScreen.show(this);
        super.onCreate(savedInstanceState);
    }
}
```
- Create a folder in `android/app/src/main/res/layout` & a file called `launch_sreen.xml` in it
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent" android:background="@color/splash_blue">
    <ImageView android:layout_width="200dp" android:layout_height="200dp" android:layout_gravity="center" android:src="@drawable/launch_screen" android:scaleType="centerCrop" />
</FrameLayout>
```
- To add the image, create a `android/app/src/main/res/drawable-xxhdpi`  & add a image called `launch_screen.png`
- Create a `app/src/main/res/values/colors.xml` file and add `primary_dark` and `splash_blue colors`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="primary_dark">#000000</color>
    <color name="splash_blue">#1D84B5</color>
</resources>
```
- Tab for analytics [Victory](https://formidable.com/open-source/victory/docs/native/)
- This has React Native SVG support
```
yarn add victory-native
# or
npm install victory-native
```
- Use lodash for data manipulation
```
yarn add lodash
# or
npm install lodash
```
- Lodash doesn't come with TypeScript types by default so [community-maintained-types](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/lodash)
```
yarn add @types/lodash --dev
# or
npm i --save-dev @types/lodash
```
