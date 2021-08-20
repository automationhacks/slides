# Introduction to appium

## What is appium?📱

- Open source library to drive mobile apps (native, hybrid and mobile web apps on Android or iOS)
  and desktop
- Choose language of your choice (`Java, Python, JavaScript, Ruby, C#` ... 🆓)
- Does not reinvent the wheel and wraps automation libraries:
  - Google `UI Automator2/Espresso`
  - Apple `XCUITest/UIAutomation`
  - Windows `WinApp`
- No requirement of SDK or recompilation of the app
- Compliant with Web driver protocol
- Works on all platforms (Windows, Mac, Linux)

## Core concepts

- Client server architecture
- Session
- Desired capabilities
- Appium Server
- Appium Clients
- Appium Desktop

![Appium request flow](images/appium-request-flow.png)

### Client server

Appium is a **web server** that exposes **REST APIs**

Typical flow

- Server receives connection from client
- Server listens for commands
- Client makes a request to Server which gets executed on device
- Server returns an HTTP response

### Session

- Each action happens within a **sessions** context
- We start a session with a `Desired capabilities` object to specify the type of connection we want

### Desired capabilities

- **Hash map** with key being different capabilities and values with specific configurations

### Appium Server

- `Node.js` server that bridges commands to native frameworks from vendors (Google, Apple)

### Appium Clients

- Clients that adhere to **WebDriver protocol** and exposes actions
- Test code uses these clients to perform desired actions on devices

### Appium Desktop

- Desktop app to support identifying elements and aid writing automated tests

## References

- [Introduction to Appium](http://appium.io/docs/en/about-appium/intro/?lang=en)
