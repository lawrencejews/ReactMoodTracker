# MoodTracker
##### Course website: [MoodTracker](https://kadikraman.github.io/react-native-beyond-basics/)
- Run to start metro server -> npx react-native start
- Open android studio then build -> npx react-native run android
- Using react navigation library: `yarn add @react-navigation/native react-native-screens react-native-safe-area-context @react-navigation/bottom-tabs` or
`npm install @react-navigation/native react-native-screens react-native-safe-area-context @react-navigation/bottom-tabs`
- Add this piece for Android development in the ` MainActivity.java `file `android/app/src/main/java/moodtracker/MainActivity.java`: 
``` 
@Override
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(null);
} 
```
- then Add this import to the top of the same file: `import android.os.Bundle;`
- Remember that turning ` "skipLibCheck": true `in tsconfig only run on the code written.