# Steps to reproduce

`npm install -g eas-cli@3.5.0`
`npx create-expo-app expo-update-bugs`
`cd expo-update-bugs`
`npx expo install expo-dev-client`
<!-- `npx expo install react-native-maps` -->
`npx expo install @react-native-firebase/app @react-native-firebase/storage`
`npx expo install expo-google-sign-in `
`eas build --platform ios --clear-cache`
FAIL!

## Run expo doctor:
Running "expo doctor"
- Finding all copies of expo-modules-autolinking
- Finding all copies of @expo/config-plugins
[stderr] [02:35:04] Expected package @expo/config-plugins@^5.0.2
[stderr] [02:35:04] Found invalid:
[stderr] [02:35:04]   @expo/config-plugins@4.1.5
[stderr] [02:35:04]   (for more info, run: npm why @expo/config-plugins)
- Finding all copies of @expo/prebuild-config
- Finding all copies of @unimodules/core
- Finding all copies of @unimodules/react-native-adapter
- Finding all copies of react-native-unimodules
Command "expo doctor" failed.
bash exited with non-zero code: 1

## Install pods
Using Expo modules
[Expo] Enabling modular headers for pod ExpoModulesCore
Auto-generating `.xcode.env.local` with $NODE_BINARY=/Users/expo/.nvm/versions/node/v16.18.1/bin/node
Adding a custom script phase for Pod RNFBApp: [RNFB] Core Configuration
Auto-linking React Native modules for target `expoupdatebugs`: RNFBApp, RNFBStorage, and react-native-maps
[Codegen] Generating ./build/generated/ios/React-Codegen.podspec.json
Analyzing dependencies
Fetching podspec for `DoubleConversion` from `../node_modules/react-native/third-party-podspecs/DoubleConversion.podspec`
[Codegen] Found FBReactNativeSpec
Fetching podspec for `RCT-Folly` from `../node_modules/react-native/third-party-podspecs/RCT-Folly.podspec`
Fetching podspec for `boost` from `../node_modules/react-native/third-party-podspecs/boost.podspec`
Fetching podspec for `glog` from `../node_modules/react-native/third-party-podspecs/glog.podspec`
Adding spec repo `trunk` with CDN `https://cdn.cocoapods.org/`
[!] CocoaPods could not find compatible versions for pod "GTMSessionFetcher/Core":
  In Podfile:
    EXGoogleSignIn (from `../node_modules/expo-google-sign-in/ios`) was resolved to 11.0.0, which depends on
      GoogleSignIn (~> 5.0.2) was resolved to 5.0.2, which depends on
        GTMSessionFetcher/Core (~> 1.1)
    RNFBStorage (from `../node_modules/@react-native-firebase/storage`) was resolved to 16.7.0, which depends on
      Firebase/Storage (= 10.3.0) was resolved to 10.3.0, which depends on
        FirebaseStorage (~> 10.3.0) was resolved to 10.3.0, which depends on
          GTMSessionFetcher/Core (< 4.0, >= 2.1)
Error: Compatible versions of some pods could not be resolved.
You are seeing this error because either:
  - Versions in the cached Podfile.lock do not match required values in Podspecs of some installed libraries. To fix this, you can re-run build command with "--clear-cache" option, or select "Clear cache and retry build" on the build page.
  - Some of the pods used in your project depend on different versions of the same pod. See logs for more information.

# Attempts to fix

delete package-lock.json
add to package.json:
`
    "resolutions": {
        "@expo/config-plugins": "^5.0.2"
    },
`
`yarn install`
`eas build --platform ios --clear-cache`

THIS FIXES EXPO DOCTOR WARNINGS. POD ERROR PERSISTS.

