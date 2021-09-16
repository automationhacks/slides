# Setup for iOS

## Step 1: Install [carthage](https://github.com/Carthage/Carthage)

- Allows to add frameworks to Cocoa applications
- Allows to build dependencies

```zsh
brew install carthage
```

## Step 2: Install [libimobiledevice](https://github.com/libimobiledevice/libimobiledevice)

- A library to communicate with services on iOS devices using native protocols.

```zsh
brew install libimobiledevice
```

## Step 3: Install [ios-deploy](https://github.com/ios-control/ios-deploy)

- Install and debug iOS apps from the command line

```zsh
brew install ios-deploy
```

## Step 4: Install [ios-webkit-debug-proxy](https://github.com/google/ios-webkit-debug-proxy)

```zsh
brew install ios-webkit-debug-proxy
```

## Step 5: Optional iOS dependencies

### IDB (iOS Device bridge)

[Instructions](https://github.com/appium/appium-idb)

```zsh
brew tap facebook/fb
brew install idb-companion
pip3.6 install fb-idb
```

## References

- [appium-xcuitest-driver](https://github.com/appium/appium-xcuitest-driver)
- [The XCUITest Driver for iOS](https://github.com/appium/appium/blob/master/docs/en/drivers/ios-xcuitest.md)
- [Real device setup](http://appium.io/docs/en/drivers/ios-xcuitest-real-devices/)
- [How to setup iOS Automation on Mac OS](https://www.youtube.com/watch?v=-_6C_-CMqSk)
- [How To Test On Real iOS Devices With Appium, Part 1](https://appiumpro.com/editions/40-how-to-test-on-real-ios-devices-with-appium-part-1)
