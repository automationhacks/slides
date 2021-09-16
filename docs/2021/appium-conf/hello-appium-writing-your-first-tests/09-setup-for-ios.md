# Setup for iOS

## Step 1: Install [carthage](https://github.com/Carthage/Carthage)

- Allows to add frameworks to Cocoa applications, allows to build dependencies

```zsh
brew install carthage
```

## Step 2: Install [libimobiledevice](https://github.com/libimobiledevice/libimobiledevice)

```zsh
brew install libimobiledevice
```

## Step 3: Install [ios-deploy](https://github.com/ios-control/ios-deploy)

```zsh
brew install ios-deploy
```

## Step 4: Install xcode-select

```zsh

sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

## Step 5: Setup WebDriverAgent

```zsh
cd /usr/local/lib/node_modules/appium/node_modules/appium-webdriveragent/
mkdir -p Resources/WebDriverAgent.bundle
sh ./Scripts/bootstrap.sh -d
```

## Step 9: Optional iOS dependencies

### IDB (iOS Device bridge)

[Instructions](https://github.com/appium/appium-idb)

```zsh
brew tap facebook/fb
brew install idb-companion
pip3.6 install fb-idb
```
