# Core concepts

- Client server architecture
- Session
- Desired capabilities
- Appium Server
- Appium Clients
- Appium Desktop

![Appium architecture](images/appium-architecture.png)

## Client server

- Appium is a web server that exposes a HTTP API
- Server receives connection from client, listens for commands, executes commands on device and
  returns an HTTP response

## Session

- Each action happens in a sessions context
- We start a session with a `Desired capabilities` object to specify the type of connection we want

## Desired capabilities

- Hash map with key being different capabilities and values with specific configurations

## Appium Server

- `Node.js` server that bridges commands to native frameworks from vendors (Google, Apple)

## Appium Clients

- Clients that adhere to WebDriver protocol and exposes actions
- Test code uses these clients to perform desired actions on devices

## Appium Desktop

- Desktop app to support identifying elements and aid writing automated tests
