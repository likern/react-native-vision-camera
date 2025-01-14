---
id: troubleshooting
title: Troubleshooting
sidebar_label: Troubleshooting
---

<div>
  <img align="right" width="35%" src="../img/11_back.png" />
</div>

Before opening an issue, make sure you try the following:

## iOS

1. Try cleaning and rebuilding **everything**:
   ```sh
   rm -rf package-lock.json && rm -rf yarn.lock && rm -rf node_modules && rm -rf ios/Podfile.lock && rm -rf ios/Pods
   npm i  # or "yarn"
   cd ios && pod repo update && pod update && pod install
   ```
2. Check your minimum iOS version. VisionCamera requires a minimum iOS version of **11.0**.
   1. Open your `Podfile`
   2. Make sure `platform :ios` is set to `11.0` or higher
3. Check your Swift version. VisionCamera requires a minimum Swift version of **5.2**.
   1. Open `project.pbxproj` in a Text Editor
   2. If the `LIBRARY_SEARCH_PATH` value is set, make sure there is no explicit reference to Swift-5.0. If there is, remove it. See [this StackOverflow answer](https://stackoverflow.com/a/66281846/1123156).
   3. If the `SWIFT_VERSION` value is set, make sure it is set to `5.2` or higher.
4. Make sure you have created a Swift bridging header in your project.
   1. Open your project (`.xcworkspace`) in Xcode
   2. Press **File** > **New** > **File** (<kbd>⌘</kbd>+<kbd>N</kbd>)
   3. Select **Swift File** and press **Next**
   4. Choose whatever name you want, e.g. `File.swift` and press **Create**
   5. Press **Create Bridging Header** when promted.
5. If you're experiencing weird behaviour, check the logs in Xcode to find out more.

## Android

1. Since the Android implementation uses the not-yet fully stable **CameraX** API, make sure you've browsed the [CameraX issue tracker](https://issuetracker.google.com/issues?q=componentid:618491%20status:open) to find out if your issue is a limitation by the **CameraX** library even I cannot get around.
2. If you're experiencing weird behaviour, check the logs in Android Studio/Logcat (<kbd>⌘</kbd> + <kbd>6</kbd>) to find out more.
3. If a camera device is not being returned by `getAvailableCameraDevices()`, make sure it meets the minimum requirements - that is minum supported harwdware level of `LIMITED` and above. See [this section in the Android docs](https://developer.android.com/reference/android/hardware/camera2/CameraDevice) for more information.

## Issues

If nothing has helped so far, try browsing the [GitHub issues](https://github.com/cuvent/react-native-vision-camera/issues?q=is%3Aissue). If your issue doesn't exist, [create a new one](https://github.com/cuvent/react-native-vision-camera/issues/new/choose). Make sure to fill out the template and include as many details as possible.
