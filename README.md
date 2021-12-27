# MoodTracker
##### Course website: [MoodTracker](https://kadikraman.github.io/react-native-beyond-basics/)
- Run to start metro server -> npx react-native start
- Open android studio then build -> npx react-native run android
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
- For Async storage locally: 
```
yarn add @react-native-async-storage/async-storage
# or
npm install @react-native-async-storage/async-storage
```
- For image rendering in production: [react-native-fast-image](https://github.com/DylanVann/react-native-fast-image)
- For vector-icons: i.e svg rendering[react-native-svg](https://github.com/react-native-svg/react-native-svg)
```
yarn add react-native-svg
# or
npm install react-native-svg
 ```
 - To clean your `.svg` use [react-svgr](https://react-svgr.com/playground/)
