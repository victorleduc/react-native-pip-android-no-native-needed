# react-native-pip-android

Add picture in picture support to react native android application.
Also has a listener to notify the pip state change.

Note: This package only works on android.

## Installation

Using npm
```sh
npm install react-native-pip-android
```

or using yarn

```sh
yarn add react-native-pip-android
```

## Setup

If you don't have to recieve updates when the pip mode is entered or exited,
you are good to go. In order to subscribe to the changes in the pip mode, add the following code to `MainActivity.java`.

Add this import to the activity

```java
...
import com.reactnativepipandroid.PipAndroidModule;


public class MainActivity extends ReactActivity {

...

@Override
  public void onPictureInPictureModeChanged (boolean isInPictureInPictureMode, Configuration newConfig) {
    PipAndroidModule.pipModeChanged(isInPictureInPictureMode);
  }
```


## Usage

```js
import PipHandler, { usePipModeListener } from 'react-native-pip-android';

export default function App() {
  // Use this boolean to show / hide ui when pip mode changes
  const inPipMode = usePipModeListener();

  if (inPipMode) {
    return (
      <View style={styles.container}>
        <Text>PIP Mode</Text>
      </View>
    );
  }

  return (
    <View style={styles.container}>
      <Text style={styles.text}>
        These text components will be hidden in pip mode
      </Text>
      <TouchableOpacity
        onPress={() => PipHandler.enterPipMode(300, 214)}
        style={styles.box}>
        <Text>Click to Enter Pip Mode</Text>
      </TouchableOpacity>
    </View>
  );
}


```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
