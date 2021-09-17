# Common libraries and setup ⚒️

## Step 1: Install homebrew

- We'll need it to install `npm` and `node`
- [Install instructions](https://docs.brew.sh/Installation)

To Install on macOS

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

> On Linux or WSL (Windows subsystem for linux): You may need to install
> [linuxbrew](https://docs.brew.sh/Homebrew-on-Linux)

## Step 2: Install node and npm

- [Instructions](https://nodejs.org/en/download/)
- Download and install node (10+) for your platform
  > Prefer choosing LTS (Long term support version)

On macOS:

```zsh
brew install node
```

- Verify running below command returns version:

```zsh
node -v
```

And verify for npm as well

```zsh
npm -v
```

## Step 3: Install Appium server

Run below command:

```zsh
npm install -g appium
```

> - 🔺 Do not use `sudo` to install appium server
> - `-g` indicates that this package would be
>   [installed globally](https://docs.npmjs.com/downloading-and-installing-packages-globally)

Verify appium server is installed

```zsh
➜  appium-fast-boilerplate git:(main) appium
[Appium] Welcome to Appium v1.17.0
[Appium] Appium REST http interface listener started on 0.0.0.0:4723
```

> You will see all server logs in this terminal window.

### Appium 2.0 🚀

To install appium 2.0

```zsh
npm install -g appium@next
```

You'll get an output like

```text
/usr/local/bin/appium -> /usr/local/lib/node_modules/appium/build/lib/main.js

> appium@2.0.0-beta.16 postinstall /usr/local/lib/node_modules/appium
> node ./postinstall.js

Not auto-installing any drivers or plugins
+ appium@2.0.0-beta.16
added 113 packages from 587 contributors, removed 316 packages, updated 136 packages and moved 5 packages in 81.611s
```

Next up, We'll install android and iOS drivers for this project

```zsh
appium driver install xcuitest
appium driver install uiautomator2
```

> You can list all available drivers using `appium driver list` Or only installed drivers using
> `appium driver list --installed`

After running `appium` command, you'll see an output like this and as you can see our installed
drivers

```text
[Appium] Welcome to Appium v2.0.0-beta.16
[Appium] Non-default server args:
[Appium]   tmpDir: /var/folders/5d/flg6q03n3j7769kffzly2x_r0000gp/T
[Appium] Attempting to load driver xcuitest...
[Appium] Attempting to load driver uiautomator2...
[Appium] Appium REST http interface listener started on 0.0.0.0:4723
[Appium] Available drivers:
[Appium]   - xcuitest@3.53.1 (automationName 'XCUITest')
[Appium]   - uiautomator2@1.67.0 (automationName 'UiAutomator2')
```

## Step 4: Install Java and set JAVA_HOME

Either install Java from oracle site or the OpenJDK version

- [Oracle download site](https://www.oracle.com/in/java/technologies/javase-downloads.html)
- [Open jdk](https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=hotspot)

On macOS:

```zsh
brew install openjdk@8
sudo ln -sfn /usr/local/opt/openjdk@8/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-8.jdk
```

Add JDK home path as `JAVA_HOME` variable

```zsh
export JAVA_HOME=/Library/Java/JavaVirtualMachines/openjdk-8.jdk/Home
export PATH=$JAVA_HOME/bin:$PATH
```

## Step 5: Verify dependencies are installed with Appium Doctor

- Appium doctor is a CLI that provides insights on what dependencies are missing as well as how to
  install them
- Make sure all required dependencies are installed

```zsh
npm install -g appium-doctor
```

Run:

```zsh
# For both android and iOS
appium-doctor
# For only android
appium-doctor --android
# For only iOS
appium-doctor --ios
```

For example:

If I run it at this point of time, it intelligently warns me about below:

![Appium Doctor](images/appium-doctor.png)

## References

- [Getting started](http://appium.io/docs/en/about-appium/getting-started/index.html#getting-started)
- [Installing Appium 2.0 and the Driver and Plugins CLI](https://appiumpro.com/editions/122-installing-appium-20-and-the-driver-and-plugins-cli)
- [Getting Started with Appium 2.0 Beta](https://applitools.com/blog/appium-2-0-beta/)
- [First Look at Appium 2.0 and New Drivers](https://www.headspin.io/blog/first-look-at-appium-2-0-and-new-drivers)
