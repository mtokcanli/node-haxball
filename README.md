[![GitHub package.json version](https://img.shields.io/github/package-json/v/wxyz-abcd/node-haxball?style=flat-square)](https://github.com/wxyz-abcd/node-haxball) [![NPM Version](https://img.shields.io/npm/v/node-haxball?style=flat-square)](https://www.npmjs.com/package/node-haxball) [![NPM Monthly Downloads](https://img.shields.io/npm/dm/node-haxball?style=flat-square)](https://npmjs.org/package/node-haxball) [![Proxy Server Status](https://img.shields.io/endpoint?label=proxy%20server&style=flat-square&url=https%3A%2F%2Fabc-haxball-proxy.up.railway.app%2Fstatus)](https://abc-haxball-proxy.up.railway.app)

[![License](https://img.shields.io/github/license/wxyz-abcd/node-haxball?style=flat-square)](LICENSE) [![Last Commit](https://img.shields.io/github/last-commit/wxyz-abcd/node-haxball?style=flat-square)](https://github.com/wxyz-abcd/node-haxball/commits/) ![Language Most Used](https://img.shields.io/github/languages/top/wxyz-abcd/node-haxball?style=flat-square) ![Repository Size](https://img.shields.io/github/repo-size/wxyz-abcd/node-haxball?style=flat-square)

[![Forks](https://img.shields.io/github/forks/wxyz-abcd/node-haxball?style=social)](https://github.com/wxyz-abcd/node-haxball/network/members) [![Stars](https://img.shields.io/github/stars/wxyz-abcd/node-haxball?style=social)](https://github.com/wxyz-abcd/node-haxball/stargazers) [![Watches](https://img.shields.io/github/watchers/wxyz-abcd/node-haxball?style=social)](https://github.com/wxyz-abcd/node-haxball/watchers)

<h1 id="title" align="center">node-haxball</h1>

<h4 align="center">node-haxball is the most powerful and lightweight bot API written by abc as a javascript library that supports both node.js and browser environments and will include every possible hack and functionality that you can imagine as a Haxball(www.haxball.com) host AND client. </h4>

### 🔖 Table Of Contents

- 🤔 [How To Use](#how-to-use)
- 🎊 [Mini-Documentation](#docs)
- 💡 [How To Contribute](#how-to-contribute)
- 🤗 [Contributors](#contributors)
- 🔏 [License](#license)

---

<h2 id="how-to-use">🤔 How To Use</h2>

#### 💻 Installing & importing as a node.js/CommonJS module:

```sh
npm install node-haxball
```
```js
const { OperationType, VariableType, ConnectionState, AllowFlags, Callback, Utils, Room, Replay, Query, RoomConfig, Plugin, Renderer, Errors, Language, Impl } = require("node-haxball")();
// Use example code here.
```

#### 💻 Usage on Browser

  - NOTE: Usage on Browser currently relies on our <a href="https://abc-haxball-proxy.up.railway.app">proxy server</a>. (Will expire at the end of each month and not work for several days.)
  - If you do not wish to use proxy server (which has some limitations), you will need our browser extension to change headers. (look at haxballOriginModifier project.)
  - <a href="https://abc-haxball-proxy.infinityfreeapp.com/?no_proxy_server=true">Alternate URL</a> (No proxy server yet.)
  - Moreover; if you have a custom backend server for Haxball, you can use it with this API too.

  #### 💻 Usage on Browser (via Proxy Server)

  ```html
  <html>
    <head>
      <script src="https://www.haxball.com/PFj3geCw/__cache_static__/g/vendor/json5.min.js"></script> <!-- json5 library -->
      <script src="https://www.haxball.com/PFj3geCw/__cache_static__/g/vendor/pako.min.js"></script> <!-- pako library -->
      <script src="https://cdn.jsdelivr.net/gh/wxyz-abcd/node-haxball@latest/src/api.js"></script> <!-- this file comes from this repo -->
    </head>
    <body>
      <script>
        var { OperationType, VariableType, ConnectionState, AllowFlags, Callback, Utils, Room, Replay, Query, RoomConfig, Plugin, Renderer, Errors, Language, Impl } = abcHaxballAPI(window, {
          proxy: {
            WebSocketUrl: "wss://abc-haxball-proxy.up.railway.app/", // These urls will (probably) work between 10th and 30th day of each month.
            HttpUrl: "https://abc-haxball-proxy.up.railway.app/rs/"
          }
        });
        // Use example code here.
      </script>
    </body>
  </html>
  ```

  #### 💻 Usage on Browser (via haxballOriginModifier Browser Extension)

  ```html
  <html>
    <head>
      <script src="https://www.haxball.com/PFj3geCw/__cache_static__/g/vendor/json5.min.js"></script> <!-- json5 library -->
      <script src="https://www.haxball.com/PFj3geCw/__cache_static__/g/vendor/pako.min.js"></script> <!-- pako library -->
      <script src="https://cdn.jsdelivr.net/gh/wxyz-abcd/node-haxball@latest/src/api.js"></script> <!-- this file comes from this repo -->
    </head>
    <body>
      <script>
        var { OperationType, VariableType, ConnectionState, AllowFlags, Callback, Utils, Room, Replay, Query, RoomConfig, Plugin, Renderer, Errors, Language, Impl } = abcHaxballAPI(window); 
        // You do not need a proxy server if you use browser's extension mechanism.
        // Use example code here.
      </script>
    </body>
  </html>
  ```

#### 💻 Example code using the library:

Joining a room:

```js

Utils.generateAuth().then(([authKey, authObj])=>{
  Room.join({
    id: "Olnit_iGRWs",
    authObj: authObj
  }, {
    storage: {
      player_name: "wxyz-abcd",
      avatar: "👽"
    }, 
    onSuccess: (room)=>{
      const { name } = room.getRoomData();
      room.sendChat("Hello " + name);
    }
  });
});
```

Creating a room:

```js

Room.create({
  name: "room123", 
  password: "password", 
  showInRoomList: true, 
  maxPlayerCount: 8,
  token: "thr1.AAAAAGNMOokNqt3forXs_Q.3qQMuLQOS9o"
}, {
  storage: {
    player_name: "wxyz-abcd",
    avatar: "👽"
  }, 
  onSuccess: (room)=>{
    const { name } = room.getRoomData();
    room.sendChat("Hello " + name);
    room.onAfterRoomLink = (roomLink)=>{
      console.log("room link:", roomLink);
    };
  }
});
```

---

<h2 id="docs">📰 Mini-Documentation</h2>

- `Library constructor(object, config)`: Initializes the library with given parameters.
  - `object`: These are objects/functions that directly affect the core functionalities. You should usually pass "window" here, because most of these objects reside there.
    - `setTimeout`, `clearTimeout`, `setInterval`, `clearInterval`, `requestAnimationFrame`, `cancelAnimationFrame`, (if you are on a custom environment such as NW.js or Electron, these functions should be binded to browser's window object before being passed on.)
    - `console`, `performance`, `crypto`, (browser's window object should have these objects as well.)
    - `RTCPeerConnection`, `RTCIceCandidate`, `RTCSessionDescription`, `WebSocket`, `XMLHttpRequest`, (these classes are used by Haxball for communication, browser's window object should have these classes as well.)
    - `JSON5`, `pako`. (These are two external libraries required by Haxball.)
  - `config`: Custom configuration for backend/proxy server. Valid object keys are;
    - `backend`: Custom backend configuration. Valid object keys are:
      - `hostname`: backend's main domain url address. Defaults to: `www.haxball.com`.
      - `hostnameWs`: backend's url address for websocket connections. Defaults to: `p2p.haxball.com`.
      - `secure`: determines whether the url is using secure protocol(`true`) or not(`false`). Defaults to: `true`.
    - `proxy`: Proxy server configuration. Valid object keys are:
      - `WebSocketChangeOriginAllowed`: browsers' websocket libraries do not allow origin change for security reasons, so we need a proxy server to change the websocket request's origin for us. If `true`, we do not need a proxy server. (we can do that in NW.js, for example)
      - `WebSocketUrl`: proxy websocket url address to use when trying to create or join a room. should end with a `/`. Is appended `host` or `client` at the end while being used. Defaults to: `wss://p2p.haxball.com/` for host and `wss://p2p2.haxball.com/` for client.
      - `HttpUrl`: proxy http url address to use when trying to create or join a room. should end with a `/`. Is appended `host` or `client` at the end while being used. Defaults to: `https://www.haxball.com/rs/`.
    - `fixNames`: fix some important variable names or not. Defaults to: `true`.
    - `version`: Haxball's expected version number. Defaults to: `9`.

- `OperationType`: Different types of operations that are being used by Haxball. Should be used to understand what kind of message we are dealing with inside callback `onOperationReceived`.
- `VariableType`: Different types of variables that can be defined in a Plugin or a Renderer with its corresponding `defineVariable` function. Should be used in a GUI environment.
- `ConnectionState`: Different connection state values. Should be used while joining a room using `Room.join`.
- `AllowFlags`: These flags allow us to understand whether a plugin or a roomConfig is able to work correctly while joining or creating a room. Especially useful in a GUI environment.

- `Language`: Methods for global language handling. (Look inside `src/defaultLanguage.js` for usage example.)
  - `add(abbr, errorsMap, rendererTextMap)`: Adds a new language with given properties. `abbr` is auto-transformed into upper-case. `errorsMap` must be an `object` that has a description function for each error code where each function returns a string. `rendererTextMap` must be an `object` that maps each `rendererTextIndex` to a `string` value. throws error while trying to add an already-existing language.
  - `remove(abbr)`: Removes the language with given abbreviation(`abbr`). `abbr` is auto-transformed into upper-case. throws error while trying to remove a non-existent or current language.
  - `current`: This is the abbreviation of the current language. Defaults to `'GB'`. It is possible to change the language of the whole API by changing this value directly; throws error if language does not exist.
  - `currentData`: read-only. Returns all name mappings for the current language, namely `errorsMap` and `rendererTextMap` that are already described in `Language.add` above.
  - `indices`: read-only. Returns the global name-to-integer mappings that shortly describe the language string.
    - `ErrorCodes`: Name-to-integer mapping that shortly describes the error codes used in `HBError` class. Note that this is the same object as `Error.ErrorCodes`.
    - `RendererTextIndices`: Name-to-integer mapping that shortly describes the default renderer's language text indices used inside the current default renderers.

- `Errors`: Global error handling objects.
  - `ErrorCodes`: Name to integer mapping that shortly describes the error codes used in `HBError` class.
  - `HBError`: This is the class that is instantiated while any error is thrown from this API.
    - `properties`:
      - `code`: The error code that has been thrown. (`integer`)
      - `params`: Parameters for the error. (`array`)
    - `functions`:
      - `toString()`: Returns the full description of the current error object by executing `currentLanguage.errorsMap[this.code](...this.params)`.

- `Callback`: Global functions to add/remove callbacks.
  - `add(eventName, metadata)`: creates all callbacks about a new event called `eventName` which should start with a capital letter. `metadata` is not used, but this is the library's current metadata structure: `{ params: array of string }`. should be used (and maybe overridden for usage of `metadata`) in a gui application to define custom event callbacks related to gui events such as keyboard, mouse, touch, timer etc. the main event callback defined in this room object to trigger all callbacks is `"_on" + eventName`.
  - `remove(eventName)`: destroys the callbacks created by `Callback.add`.

- `Replay`: Functions/classes related to replays.

  - `read(uint8Array, callbacks, options)`: Creates and returns a non-blocking replay reader object. 

    - Parameters: 
      - `uint8Array`: Must be an Uint8Array containing the contents of a .hbr file. (Currently, only version 3 is supported.)
      - `callbacks`: An object that has the same callbacks as the renderer template. (except callbacks that are related to customEvents, roomConfigs, plugins, renderers, language; due to replay files not containing its corresponding event.) (Look at examples/api_structure/replayReader.js for all supported callbacks and example usage.)
      - `options`: An object that may contain the following keys:
        - `requestAnimationFrame`: Override function for `requestAnimationFrame`. (`null` = use library's default `requestAnimationFrame`.)
        - `cancelAnimationFrame`: Override function for `cancelAnimationFrame`. (`null` = use library's default `cancelAnimationFrame`.)
        - `fps_limit`: Any positive number that will be used as the fps limit. (`null` = no limit)

    - Returning replay reader object:
      - properties:
        - `roomData`: An object containing all information about the current room state.
      - functions:
        - `length()`: Returns the length of replay content in milliseconds.
        - `getTime()`: Returns the current time in milliseconds.
        - `setTime(destinationTime)`: Plays the replay until the `destinationTime`(in milliseconds) or end of replay is reached. Note that it may take some time to reach the destination time(especially if you are trying to rewind time), because the game state data is generated on the fly and not stored in memory. (It would probably use huge amounts of RAM.)
        - `setSpeed(coefficient)`: Changes the speed of playing the replay. `coefficient` must be a real number >=0. 
          - `coefficient` = 0 : stop replay.
          - 0 < `coefficient` < 1 : slow-motion replay.
          - `coefficient` = 1 : normal speed replay.
          - `coefficient` > 1 : fast-motion replay.
        - `destroy()`: Frees the resources that are used by this object.
      - callbacks:
        - `onDestinationTimeReached()`: Destination time has been reached. Runs after a call to `setTime(destinationTime)`.
        - `onEnd()`: The end of replay data has been reached.

- `Utils`: Some static utility functions.

  - `generateAuth()`: generates a new `player_auth_key` along with its companion auth object. you should store the key and use it later if you want to be recognized in Haxball rooms. the object is used in `Room.join`. returns `Promise([authKey, authObj])`
  - `authFromKey(authKey)`: recreates the auth object for given `authKey`. the object is used in `Room.join`. returns `Promise(authObj)`
  - `getRoomList()`: returns the current room list. returns `Promise(roomListArray)`
  - `numberToColor(number)`: returns the html color string (rgba representation) of the given `number`. (0 <= `number` <= 16777215)
  - `colorToNumber(color)`: returns the number representation of the given html color string (rgba representation).
  - `keyState(dirX, dirY, kick)`: returns an integer key state value to be used in `Room.setKeyState`. `dirX` = oneof\[`-1`:left, `0`:still, `1`:right\], `dirY` = oneof\[`-1`:up, `0`:still, `1`:down\], `kick` = `true`/`false`.
  - `getGeo()`: connects to Haxball's geolocation API to get your location based on IP address. you can use it directly as `geo` key inside `storage` object. returns `Promise(geoLocationObject)`
  - `getDefaultStadiums()`: get default stadium array.
  - `parseStadium(textDataFromHbsFile, onError)`: parse text as a stadium object and return it.
  - `exportStadium(stadium)`: generate and return text(.hbs) content from a `stadium` object.

- `Query`: Static functions to query map features. For now, `roomState` has to come from either `Room.getRoomDataOriginal` or the extrapolated parameter in `Renderer.render`.
  - `getVertexIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first vertex that has a distance to `mapCoordinate` lower than `threshold`.
  - `getVertexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the first vertex that has a distance to `mapCoordinate` lower than `threshold`.
  - `getSegmentIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first segment that has a distance to `mapCoordinate` lower than `threshold`.
  - `getSegmentAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the first segment that has a distance to `mapCoordinate` lower than `threshold`.
  - `getGoalIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first goal that has a distance to `mapCoordinate` lower than `threshold`.
  - `getGoalAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the first goal that has a distance to `mapCoordinate` lower than `threshold`.
  - `getPlaneIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first plane that has a distance to `mapCoordinate` lower than `threshold`.
  - `getPlaneAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the first plane that has a distance to `mapCoordinate` lower than `threshold`.
  - `getJointIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first joint that has a distance to `mapCoordinate` lower than `threshold`.
  - `getJointAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the first joint that has a distance to `mapCoordinate` lower than `threshold`.
  - `getDiscIndexAtMapCoord(roomState, mapCoordinate)`: Finds the index of the first disc that includes `mapCoordinate`.
  - `getDiscAtMapCoord(roomState, mapCoordinate)`: Finds the first disc that includes `mapCoordinate`.
  - `getSpawnPointIndexAtMapCoord(roomState, mapCoordinate, threshold)`: Finds the index of the first spawn point that has a distance to `mapCoordinate` lower than `threshold`. Returns `[spawnPointIndex, teamId]`. `teamId`: \[`1`: red team, `2`: blue team.\]

- `Room`: The class that currently hosts all room operations. Should only be initialized by either `Room.join` or `Room.create`.
  - `static functions`: These functions are used to create/join a room.
    - `create(createParams, commonParams)`: create a room with given parameters.
      - `createParams`:
        - `name`: name of the room.
        - `password`: password to protect the room. can be set `null`/`undefined` for no password.
        - `token`: get a recaptcha token from `www.haxball.com/headlesstoken` and write it here to bypass the loop of trying to solve recaptcha.
        - `noPlayer`: set it to `true` if you are planning to host the room without actually playing the game, otherwise set it to `false`.
        - `geo`: `{lat: latitude(number), lon: longitude(number), flag: 2 letter country flag(string)}` geolocation values of the room about to be created.
        - `playerCount`: if set to a `number`, always fixes the player count to this specific `number`.
        - `maxPlayerCount`: the maximum allowed player count in the room.
        - `unlimitedPlayerCount`: if set to `true`, bypasses the player count controller.
        - `fakePassword`: if set to `true`, the room will show that it is password-protected while in fact it is not.
        - `showInRoomList`: set to `true` if you want this room to show up in the room list.
        - `onError(error, clientConnectionObj)`: called when an exception is thrown from the room. clientConnectionObj is the connection object of the client that caused the exception. the connection will be closed just after this callback is executed.
      - `commonParams`: explained below in `Room.join`.

    - `join(joinParams, commonParams)`: try to join the room(`roomId`) with given `password`(or `null`=no password). returns `Promise(room)` which is rejected if failed.
      - `joinParams`:
        - `id`: the id of the room to join. for example, if the room link is `https://www.haxball.com/play?c=31IBNI3w4F0`, this room's id is `31IBNI3w4F0`.
        - `password`: a password value to join the room if the room is password-protected.
        - `token`: if the room is recaptcha-protected, you have to use a client token. currently there is not any other clean way of doing this except using the NW.js token generator project, so you might want to look at it.
        - `authObj`: an auth object that has to be initialized by `Utils.generateAuth()` or `Utils.authFromKey()` before being used here.
      - `commonParams`:
        --- properties section ---
        - `storage`:
          - `crappy_router`: if `true`, sets some timeout value to `10` seconds instead of `4` seconds while joining a room.
          - `extrapolation`: use the future(+) or past(-) values of game state while rendering or other kinds of processing. this value should be a number between `-200`ms and `+200`ms.
          - `fps_limit`: if `1`, fps limit is set to 30, otherwise no limit is set.
          - `player_name`: name of the player. default value is `"abc"`.
          - `avatar`: avatar of the player. default value is `null`.
          - `geo`:
            - `lat`: latitude value (number, default value is `40`).
            - `lon`: longitude value (number, default value is `40`).
            - `flag`: 2 letter country code (string, default value is `"tr"`).
          - `onValueSet(key, value)`: a callback function that is called just after the value of a key of this object has been changed by this library. default value is `null`.
        - `noPluginMechanism`: if `true`, renderer and plugin mechanism will not work. Should only be used for optimal performance. You have to define `Room._onXXXXXX` callbacks by yourself.
        - `useDefaultChatCommandMechanism`: if `false`, you will have to write `onBeforeOperationReceived` and `onAfterOperationReceived` callbacks by yourself. By default, `onBeforeOperationReceived` is a function that determines whether a chat message is a command or not by looking at the chat message's first character(should be '!'); and `onAfterOperationReceived` is a function that blocks these command messages from being sent to the clients. All plugins can run their own `onOperationReceived` after this `onBeforeOperationReceived` function call, and all of them can block/modify all messages before the messages reach to `onAfterOperationReceived`.
        - `config`: the `RoomConfig` object that contains all the main callbacks of this room. the object should be derived from the provided `RoomConfig` class. default value is `null`. (Look at examples/roomConfigs/method2 folder for example RoomConfigs to use here, or src/roomConfigTemplate_method2.js for a template RoomConfig that contains all callbacks.)
        - `renderer`: the `Renderer` object that can render the game. the object should be derived from the provided `Renderer` class. default value is `null`. (Look at examples/renderers folder for example RoomConfigs to use here, or src/rendererTemplate.js for a template Renderer that contains all callbacks.)
        - `plugins`: array of `Plugin` objects to be used. the objects should be derived from the provided `Plugin` class. default value is `[]`. (Look at examples/plugins folder for example Plugins to use here, or src/pluginTemplate.js for a template Plugin that contains all callbacks.)
        - `version`: Haxball's version number. other clients cannot join this room if their version number is different than this number. default value is `9`.
        - `kickTimeout`: when you kick the ball, it causes you to release kick button by default. this library changes it so that it causes a timeout that makes you automatically press kick button again. you may assign a negative value to disable this feature. default value is `20`(msec).

        --- event callbacks section ---
        - `onSuccess(room)`: joined/created `room`.
        - `onFailure(error)`: join room failed with error(`error`).
        - `onLeave(msg)`: triggered while leaving the room with reason(`msg`).
        - `onConnectionStateChange(state)`: connection state has just changed to (`state`).
        - `onReverseConnection()`: trying reverse connection while joining a room.
        - `onRequestRecaptcha()`: recaptcha is required while joining or creating a room.

        --- event triggers section ---
        - `cancel()`: should be used to cancel the process of joining a room.
        - `useRecaptchaToken(token)`: should be used to send the recaptcha token after `onRequestRecaptcha` event occurred. currently only working while creating a room. workaround: in order to send the token to try and join a recaptcha-protected room, cleanup old resources and use `Room.join` with the new token.
    
    - `sandbox(callbacks, options)`: creates a sandbox room.
    
      - Parameters: 
        - `callbacks`: An object that has the same callbacks as the renderer template.
        - `options`: An object that may contain the following keys:
          - `controlledPlayerId`: Id of the player to be controlled.
          - `requestAnimationFrame`: Override function for `requestAnimationFrame`. (`null` = use library's default `requestAnimationFrame`.)
          - `cancelAnimationFrame`: Override function for `cancelAnimationFrame`. (`null` = use library's default `cancelAnimationFrame`.)
          - `fps_limit`: Any positive number that will be used as the fps limit. (`null` = no limit)
      
      - Returning sandbox room object:
        - properties:
          - `roomData`: An object containing all information about the current room state. Note that this object also has all of the functions explained below in section: `sandbox mode functions`. (it only has `copy()` instead of `takeSnapshot()`)
        - functions:
          - `setSimulationSpeed(coefficient)`: Changes the speed of the simulation. `coefficient` must be a real number >=0.
            - `coefficient` = 0 : stop simulation.
            - 0 < `coefficient` < 1 : slow-motion simulation.
            - `coefficient` = 1 : normal speed simulation.
            - `coefficient` > 1 : fast-motion simulation.
          - `runSteps(count)`: runs the simulation `count` steps. simulation must be stopped for this function to work.
          - `takeSnapshot()`: returns a complete snapshot of the current room state.
          - `useSnapshot(newRoomState)`: sets the current room state reference to `newRoomState`. `newRoomState` should be created by `takeSnapshot()` first.
          - `getRoomDataOriginal()`: get the most important original objects that has the current room data. (added for compatibility with normal rooms.)
          - `playerJoin(id, name, flag, avatar, conn, auth)`: adds a new player with properties(`id`, `name`, `flag`, `avatar`, `conn`, `auth`) to the room.
          - `playerLeave(playerId)`: removes player(`playerId`) from the room.
          - `playerInput(input, byId)`: sets the input of player(`byId`) to `input`.
          - `playerChat(msg, byId)`: writes chat message(`msg`) as player(`byId`).
          - `setKeyState(state)`: set current key state to `state`. (added for compatibility with normal rooms.)
          - `setPlayerChatIndicator(value, byId)`: sets the chat indicator status of player(`byId`) to `value`.
          - `setPlayerAvatar(value, byId)`: sets the avatar of player(`byId`) to `value`.
          - `setCurrentStadium(value, byId, onError)`: creates and applies a fake event by player(`byId`) to set the current stadium to `stadium`.
          - `sendAnnouncement(msg, color=-1, style=0, sound=1, targetId, byId)`: send announcement message(`msg`) to player(`targetId`) with properties(`color`, `style`, `sound`). `targetId` is `null` -> send to everyone. `byId` must be `0`.
          - `startGame(byId)`: creates and applies a fake event by player(`byId`) to start the game.
          - `stopGame(byId)`: creates and applies a fake event by player(`byId`) to stop the game.
          - `setGamePaused(value, byId)`: creates and applies a fake event by player(`byId`) to set the game's paused state to `value`.
          - `setScoreLimit(value, byId)`: creates and applies a fake event by player(`byId`) to set the game's score limit to `value`.
          - `setTimeLimit(value, byId)`: creates and applies a fake event by player(`byId`) to set the game's time limit to `value`.
          - `setTeamsLock(value, byId)`: creates and applies a fake event by player(`byId`) to set the game's teams lock state to `value`.
          - `autoTeams(byId)`: creates and applies a fake event by player(`byId`) to remove last 2 players from spectators and add them to teams.
          - `setPlayerTeam(playerId, teamId, byId)`: creates and applies a fake event by player(`byId`) to set player(`playerId`)'s team to team(`teamId`).
          - `setKickRateLimit(min, rate, burst, byId)`: creates and applies a fake event by player(`byId`) to set the room's kick rate limit.
          - `setTeamColors(teamId, angle, colors, byId)`: creates and applies a fake event by player(`byId`) to set the team colors for team(`teamId`). `teamId`: `1`(red) | `2`(blue), `angle`: `integer`, `colors`: maximum 4 parseable(hex-rgb) color parameters.
          - `setPlayerAdmin(playerId, value, byId)`: creates and applies a fake event by player(`byId`) to set player(`playerId`)'s admin status to `isAdmin`.
          - `kickPlayer(playerId, reason, ban, byId)`: creates and applies a fake event by player(`byId`) to kick/ban a player(`playerId`) with reason(`reason`).
          - `setPlayerSync(value, byId)`: set the sync of player(`byId`) to `value`.
          - `sendPingData(valueFunc, byId)`: creates and applies a fake event by player(`byId`) to change all ping values with `valueFunc`. `byId` must be `0`.
          - `setDiscProperties(discId, type, data, byId)`: creates and applies a fake event by player(`byId`) to set disc(`discId`) properties to `data`. `byId` must be `0`.
          - `sendCustomEvent(type, data, byId)`: creates and applies a fake custom event with properties(`type`, `data`) by player(`byId`).
          - `destroy()`: Frees the resources that are used by this object.

  - `properties`:
    - `isHost`: `true` for hosts, `false` for clients
    - `client`: a reference to an inner client object that the event callbacks before room was created are attached to.
    - `currentPlayerId`: current player's id
    - `currentPlayer`: the original current player object
    - `sdp`: current room's sdp value (only for client rooms)
    - `kickTimeout`: time between releasing and re-pressing the kick key (in milliseconds, defaults to `20`)
    - `renderer`: room's current renderer object
    - `plugins`: array of all available plugins. this is used internally to restore the order of plugins while plugin activation/deactivation.
    - `activePlugins`: array of currently active plugins. this is used internally for callbacks.
    - `pluginsMap`: all available plugins mapped as `pluginsMap[plugin.name] = plugin`, for optimized use to communicate between plugins.

  - `functions`:
    - `leave()`: leaves the room.
    - `setProperties({ name, password, geo: { lat, lon, flag }, playerCount, maxPlayerCount, fakePassword })`: sets the room's properties.
    - `setRecaptcha(on)`: sets the room's recaptcha mode. `on`: `true`/`false`.
    - `setKickRateLimit(min, rate, burst)`: sets the room's kick rate limit.
    - `setHandicap(handicap)`: sets the player's `handicap` value in msecs.
    - `setExtrapolation(extrapolation)`: sets the client's `extrapolation` value in msecs.
    - `clearBans()`: clears all bans. host-only.
    - `setAvatar(avatar)`: sets the current player's client `avatar`.
    - `setPlayerAvatar(id, value, headless)`: sets the avatar of player(`id`) to `avatar`. `headless` is a boolean to determine whether the headless or client avatar is being set. host-only.
    - `setChatIndicatorActive(active)`: sets the current player's chat indicator status. `active`: `true`/`false`.
    - `setTeamColors(teamId, angle, ...colors)`: sets the team colors for team(`teamId`). `teamId`: `1`(red) | `2`(blue), `angle`: `integer`, `colors`: maximum 4 parseable(hex-rgb) color parameters.
    - `setUnlimitedPlayerCount(on)`: adds or removes player limit control. host-only. `on`: `true`/`false`.
    - `setFakePassword(fakePwd)`: sets a fake value for room's password status. host-only. `fakePwd`: `true`/`false` or `null` to disable.
    - `sendChat(msg, targetId)`: send chat message(`msg`) to player(`targetId`). `targetId` is `null` -> send to everyone. `targetId` is host-only.
    - `sendAnnouncement(msg, targetId, color, style, sound)`: send announcement message(`msg`) to player(`targetId`) with properties(`color`, `style`, `sound`). `targetId` is `null` -> send to everyone. host-only.
    - `setDiscProperties(discId, properties)`: set disc(`discId`) `properties`. host-only.
    - `setPlayerDiscProperties(playerId, properties)`: set player(`playerId`)'s disc `properties`. host-only.
    - `reorderPlayers(playerIdList, moveToTop)`: remove all players with ids in `playerIdList` and re-add them in the given order to the (top or bottom)(`moveToTop`) of the player list. host-only.
    - `sendCustomEvent(type, data)`: sends a `CustomEvent(type, data)` that can only be received by the users of this modified client.
    - `getKeyState()`: get current key state.
    - `setKeyState(state)`: set current key state to `state`.
    - `startGame()`: start game.
    - `stopGame()`: stop game.
    - `pauseGame()`: toggle pause/resume game.
    - `isGamePaused()`: returns `true` if game is paused.
    - `autoTeams()`: remove last 2 players from spectators and add them to teams.
    - `lockTeams()`: toggle lock/unlock the ability to change teams.
    - `resetTeams()`: move everyone to spectators.
    - `randTeams()`: remove random 2 players from spectators and add them to teams.
    - `resetTeam(teamId)`: move everyone on team(`teamId`) to spectators.
    - `setSync(value)`: set synchronized status to `value` which must be `true` or `false`. host-only.
    - `setCurrentStadium(stadium, onError)`: set current map(`stadium`).
    - `setTimeLimit(value)`: set time limit(`value`).
    - `setScoreLimit(value)`: set score limit(`value`).
    - `changeTeam(teamId)`: set current player's team(`teamId`).
    - `setPlayerTeam(playerId, teamId)`: set player(`playerId`)'s team to team(`teamId`).
    - `setPlayerAdmin(playerId, isAdmin)`: set player(`playerId`)'s admin status to `isAdmin`.
    - `kickPlayer(playerId, reason, isBanning)`: kick/ban a player(`playerId`) with reason(`reason`).
    - `getPlayerOriginal(id)`: get original player data object for player(`id`).
    - `getPlayer(id)`: get a new and structured player data object for player(`id`).
    - `getPlayersOriginal()`: get the original players array.
    - `getPlayers()`: get a new and structured players array.
    - `getBallOriginal(extrapolated = true)`: get the original ball object.
    - `getBall(extrapolated = true)`: get a new and structured ball object.
    - `getDiscsOriginal(extrapolated = true)`: get the original disc object for disc(`discId`).
    - `getDiscs(extrapolated = true)`: get a new and structured disc object for disc(`discId`).
    - `getDiscOriginal(discId, extrapolated = true)`: get the original disc object for disc(`discId`).
    - `getDisc(discId, extrapolated = true)`: get a new and structured disc object for disc(`discId`).
    - `getPlayerDiscOriginal(playerId, extrapolated = true)`: get the original disc object for player(`playerId`).
    - `getPlayerDisc(playerId, extrapolated = true)`: get a new and structured disc object for player(`playerId`).
    - `getPlayerDiscOriginal_exp(playerId)`: get the original disc object for player(`playerId`). faster than `getPlayerDiscOriginal`, but experimental. use at your own risk.
    - `getPlayerDisc_exp(playerId)`: get a new and structured disc object for player(`playerId`). faster than `getPlayerDisc`, but experimental. use at your own risk.
    - `getRoomDataOriginal()`: get the most important original objects that has the current room data.
    - `getRoomData(extrapolated = true)`: get a new and structured room data object that has some of the current room data.
    - `getCurrentMap()`: get the original object of the current map.
    - `mapChecksum(map)`: calculate checksum for given map object. returns `null` for original maps.
    - `setPluginActive(name, active)`: activate/deactivate the plugin(`name`).
    - `startRecording()`: start recording replay data. returns `true` if succeeded, `false` otherwise. recording should not be started before calling this.
    - `stopRecording()`: stop recording replay data. returns `UIntArray8` data if succeeded, null otherwise. recording should be started before calling this.
    - `isRecording()`: returns `true` if recording has started; `false` otherwise.
    - `setConfig(roomConfig)`: sets the `RoomConfig` object that contains all the main callbacks of this room. the `roomConfig` object should be derived from the provided `RoomConfig` class.
    - `mixConfig(newRoomConfig)`: adds all callbacks in `newRoomConfig` into the room's current RoomConfig object. if there are callbacks with the same name, a new callback is created that calls both of them. (current callback is called first.)
    - `updatePlugin(pluginIndex, newPluginObj)`: sets the `Plugin` at the specified `pluginIndex` to the `newPluginObj` object, initialization and activation are automatic. plugin names must be the same. the plugin object should be derived from the provided `Plugin` class.
    - `setRenderer(renderer)`: sets the `Renderer` object that will render the game. the `renderer` object should be derived from the provided `Renderer` class.

  - `sandbox mode functions`: these functions are not supported by the original Haxball client. you would need to create `CustomEvent`s to use them within a synchronized(network) environment. the game must NOT be stopped for these functions to work.
    - `takeSnapshot()` : returns a snapshot of the current game state. you can load this object directly into sandbox using its `useSnapshot(newRoomState)` function.
    - `exportStadium()` : returns all current game objects in hbs format.
    - `createVertex(data)` : creates a vertex object in memory. `data`: `{ x: number, y: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `createSegment(data)` : creates a segment object in memory using vertex indices. `data`: `{ v0: number, v1: number, color: ("transparent" || string || [r: number, g: number, b: number]), bias: number, (curve: number || curveF: number), vis: boolean, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `createSegmentFromObj(data)` : creates a segment object in memory using vertex objects. `data`: `{ v0: vertexObj, v1: vertexObj, color: ("transparent" || string || [r: number, g: number, b: number]), bias: number, (curve: number || curveF: number), vis: boolean, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `createGoal(data)` : creates a goal object in memory. `data`: `{ p0: [x: number, y: number], p1: [x: number, y: number], team: ("red" || "blue") }`
    - `createPlane(data)` : creates a plane object in memory. `data`: `{ normal: [x: number, y: number], dist: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `createDisc(data)` : creates a disc object in memory. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, color: ("transparent" || string || [r: number, g: number, b: number]), bCoef: number, cMask: array of string, cGroup: array of string }`
    - `createJoint(data)` : creates a joint object in memory using disc indices. `data`: `{ d0: number, d1: number, color: ("transparent" || string || [r: number, g: number, b: number]), strength: "rigid" || number, length: null || number || [min: number, max: number] }`
    - `createJointFromObj(data)` : creates a joint object in memory using disc objects. `data`: `{ d0: discObj, d1: discObj, color: ("transparent" || string || [r: number, g: number, b: number]), strength: "rigid" || number, length: null || number || [min: number, max: number] }`
    - `addVertex(data)` : creates a vertex object and adds it to the current stadium. `data`: `{ x: number, y: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `addSegment(data)` : creates a segment object and adds it to the current stadium. `data`: `{ v0: number, v1: number, color: ("transparent" || string || [r: number, g: number, b: number]), bias: number, (curve: number || curveF: number), vis: boolean, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `addGoal(data)` : creates a goal object and adds it to the current stadium. `data`: `{ p0: [x: number, y: number], p1: [x: number, y: number], team: ("red" || "blue") }`
    - `addPlane(data)` : creates a plane object and adds it to the current stadium. `data`: `{ normal: [x: number, y: number], dist: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `addDisc(data)` : creates a disc object and adds it to the current stadium. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, color: ("transparent" || string || [r: number, g: number, b: number]), bCoef: number, cMask: array of string, cGroup: array of string }`
    - `addJoint(data)` : creates a joint object and adds it to the current stadium. `data`: `{ d0: number, d1: number, color: ("transparent" || string || [r: number, g: number, b: number]), strength: "rigid" || number, length: null || number || [min: number, max: number] }`
    - `addSpawnPoint(data)` : adds a spawn point with given properties to the current stadium. `data`: `{ x: number, y: number, team: ("red" || "blue") }`
    - `addPlayer(data)` : adds a player with given properties to the current stadium. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, bCoef: number, cMask: array of string, cGroup: array of string, id: integer, name: string, avatar: string, flag: string, team: ("spec" || "red" || "blue") }`. these keys must exist: `team`, `id`, `name`, `avatar`, `flag`.
    - `findVertexIndicesOfSegmentObj(segmentObj)` : finds the indices of vertices that form the given segment object(`segmentObj`). return format: `[index1, index2]`.
    - `findVertexIndicesOfSegment(segmentIndex)` : finds the indices of vertices that form the `segmentIndex`th segment object. return format `[index1, index2]`.
    - `updateVertex(idx, data)` : updates the `idx`th vertex's only the given values. `data`: `{ x: number, y: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `updateSegment(idx, data)` : updates the `idx`th segment's only the given values. `data`: `{ v0: number, v1: number, color: ("transparent" || string || [r: number, g: number, b: number]), bias: number, (curve: number || curveF: number), vis: boolean, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `updateGoal(idx, data)` : updates the `idx`th goal's only the given values. `data`: `{ p0: [x: number, y: number], p1: [x: number, y: number], team: ("red" || "blue") }`
    - `updatePlane(idx, data)` : updates the `idx`th plane's only the given values. `data`: `{ normal: [x: number, y: number], dist: number, bCoef: number, cMask: array of string, cGroup: array of string }`
    - `updateDisc(idx, data)` : updates the `idx`th disc's only the given values. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, color: ("transparent" || string || [r: number, g: number, b: number]), bCoef: number, cMask: array of string, cGroup: array of string }`
    - `updateDiscObj(discObj, data)` : updates the given disc object(`discObj`)'s only the given values. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, color: ("transparent" || string || [r: number, g: number, b: number]), bCoef: number, cMask: array of string, cGroup: array of string }`
    - `updateJoint(idx, data)` : updates the `idx`th joint's only the given values. `data`: `{ d0: number, d1: number, color: ("transparent" || string || [r: number, g: number, b: number]), strength: "rigid" || number, length: null || number || [min: number, max: number] }`
    - `updateSpawnPoint(idx, team, data)` : updates the `idx`th spawn point in team(`team`) using only the given values. `data`: `{ x: number, y: number, team: ("red" || "blue") }`
    - `updatePlayer(playerId, data)` : updates the player(`playerId`)'s only the given values. `data`: `{ pos: [x: number, y: number], speed: [x: number, y: number], gravity: [x: number, y: number], radius: number, invMass: number, damping: number, bCoef: number, cMask: array of string, cGroup: array of string, name: string, avatar: string, flag: string, team: ("spec" || "red" || "blue") }`
    - `removeVertex(idx)` : removes the `idx`th vertex from the current stadium.
    - `removeSegment(idx)` : removes the `idx`th segment from the current stadium.
    - `removeGoal(idx)` : removes the `idx`th goal from the current stadium.
    - `removePlane(idx)` : removes the `idx`th plane from the current stadium.
    - `removeDisc(idx)` : removes the `idx`th disc from the current stadium.
    - `removeJoint(idx)` : removes the `idx`th joint from the current stadium.
    - `removeSpawnPoint(idx, team)` : removes the `idx`th spawn point of team(`team`) from the current stadium. `team`: `"red" || "blue"`
    - `removePlayer(playerId)` : removes the player(`playerId`) from the current stadium.
    - `updateStadiumPlayerPhysics(data)` : updates the current stadium's only the given player physics values. `data`: `{ radius: number, gravity: [x: number, y: number], invMass: number, bCoef: number, cGroup: array of string, damping: number, kickingDamping: number, acceleration: number, kickingAcceleration: number, kickStrength: number, kickback: number }`
    - `updateStadiumBg(data)` : updates the current stadium's only the given background values. `data`: `{ type: 0("none") || 1("grass") || 2("hockey"), width: number, height: number, kickOffRadius: number, cornerRadius: number, color: ("transparent" || string || [r: number, g: number, b: number]), goalLine: number }`
    - `updateStadiumGeneral(data)` : updates the current stadium's only the given general values. `data`: `{ name: string, width: number, height: number, maxViewWidth: number, cameraFollow: 0("") || 1("player"), spawnDistance: number, kickOffReset: true("full") || false("partial"), canBeStored: boolean }`
  
  - `fake event triggers`: these functions are intended to be used in host mode to create/control in-memory bot players that will run much more efficiently than standard networking bot players. they also work for normal player objects, and can be used to create some events belonging to a player that did not originate from that player. most of these fake events also trigger an `onOperationReceived` call before being sent to clients.
    - `fakePlayerJoin(id, name, flag, avatar, conn, auth)`: triggers a fake join room event; which in turn creates a new in-memory player object. If there was a player before with this id, old resources are automatically reassigned to this new player object, and that player will wake up. 0 <= `id` <= 65535, all the other parameters must be a string. 
    - `fakePlayerLeave(id)`: triggers a fake leave room event. returns the player's properties so that you may pass them to `fakePlayerJoin` at a later time to wake that player. passing `id` = 0 causes desync on clients (because there's a special check for the case `id` = 0 in original clients). the player, although seemingly leaving the room, still watches the room, waiting for a fake player join event. all parameters except `id` may be different in the new `fakePlayerJoin` call, which allows player's `name`, `flag`, `avatar`, `conn` and `auth` to change without the player entirely leaving the room.
    - `fakeSendPlayerInput(input, byId)`: triggers a fake input(keys) event that apparently came from `player(byId)`. 0<=`input`<=31.
    - `fakeSendPlayerChat(msg, byId)`: triggers a fake chat event that apparently came from `player(byId)`. `msg` must be a string.
    - `fakeSetPlayerChatIndicator(value, byId)`: triggers a fake chat indicator change event that apparently came from `player(byId)`. `value` must be `true` or `false`.
    - `fakeSetPlayerAvatar(value, byId)`: triggers a fake avatar change event that apparently came from `player(byId)`. `value` must be a string.
    - `fakeSetPlayerAdmin(playerId, value, byId)`: triggers `player(playerId)`'s admin status change fake event that apparently came from `player(byId)`. `value` must be `true` or `false`.
    - `fakeSetPlayerSync(value, byId)`: triggers a fake player sync status change event that apparently came from `player(byId)`. `value` must be `true` or `false`.
    - `fakeSetStadium(value, byId)`:  triggers a fake stadium change event that apparently came from `player(byId)`. only works if game is stopped. `value` must be a valid stadium object.
    - `fakeStartGame(byId)`: triggers a fake game start event that apparently came from `player(byId)`.
    - `fakeStopGame(byId)`: triggers a fake game stop event that apparently came from `player(byId)`.
    - `fakeSetGamePaused(value, byId)`: triggers a fake game pause/resume event that apparently came from `player(byId)`. `value` must be `true` or `false`.
    - `fakeSetScoreLimit(value, byId)`: triggers a fake score limit change event that apparently came from `player(byId)`. `value`>=0.
    - `fakeSetTimeLimit(value, byId)`: triggers a fake time limit change event that apparently came from `player(byId)`. `value`>=0.
    - `fakeSetTeamsLock(value, byId)`: triggers a fake teams lock change event that apparently came from `player(byId)`. `value` must be `true` or `false`.
    - `fakeAutoTeams(byId)`: triggers a fake auto teams event that apparently came from `player(byId)`.
    - `fakeSetPlayerTeam(playerId, teamId, byId)`: triggers `player(playerId)`'s player team change fake event that apparently came from `player(byId)`. 0<=`teamId`<=2.
    - `fakeSetKickRateLimit(min, rate, burst, byId)`: triggers a fake kick rate limit change event that apparently came from `player(byId)`. `min`, `rate`, `burst`>=0.
    - `fakeSetTeamColors(teamId, angle, colors, byId)`: triggers `team(teamId)`'s colors change event that apparently came from `player(byId)`. 0<=`angle`<=180, `colors` must be an array of type (0 <= `integer` <= 16777215) that contains at most 4 integers.
    - `fakeKickPlayer(playerId, reason, ban, byId)`: triggers `player(playerId)`'s kick/ban fake event that apparently came from `player(byId)`. `reason` must be a string, `ban` must be `true` or `false`.

- `RoomConfig`: A class that defines a room configuration object. Room configurations should be based on this class.

  - `constructor(metadata)`: creates a new `RoomConfig` instance. `metadata` is the information that you would want to show/update inside a GUI application.

  - `abstract callbacks`: These functions should be overridden when writing a GUI application using this API before creating any `RoomConfig` object. These are defined in `RoomConfig.prototype`.
    - `defineMetadata(metadata)`: Does nothing, returns nothing by default. This function should define the given `metadata` object inside this `RoomConfig` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the default roomConfig in the examples folder uses the following `metadata` structure: `{name, version, author, description, allowFlags}`.
    - `defineVariable(variable)`: Does nothing, returns `variable`'s value by default. This function should define the given `variable` object inside this `RoomConfig` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the default roomConfig in the examples folder use the following variable structure: `{name, type, value, range, description}`. This function should return the value of the `variable`, and should be used whenever a variable whose value is changeable from outside will be defined. 

  - `modifier callbacks`:
    - `[dataArray, customData] = modifyPlayerDataBefore(playerId, name, flag, avatar, conn, auth)`: set player's data just before player has joined the room. dataArray format should be `[modifiedName, modifiedFlag, modifiedAvatar]`. if `dataArray` is `null`, player is not allowed to join. also prepares a custom data object to send to all plugins. `customData=false` means "don't call callbacks". host-only.
    - `[modifiedName, modifiedFlag, modifiedAvatar] = modifyPlayerData(playerId, name, flag, avatar, conn, auth, customData)`: set player's data just before player has joined the room. `return null` -> player is not allowed to join. host-only.
    - `[modifiedName, modifiedFlag, modifiedAvatar] = modifyPlayerDataAfter(playerId, name, flag, avatar, conn, auth, customData)`: set player's data just before player has joined the room. `return null` -> player is not allowed to join. host-only.
    - `[newPing, customData] = modifyPlayerPingBefore(playerId, ping)`: prepares a custom data object to send to all plugins while setting player's `ping`. `customData=false` means "don't call callbacks". host-only.
    - `newPing = modifyPlayerPing(playerId, ping, customData)`: set player's `ping`. host-only.
    - `newPing = modifyPlayerPingAfter(playerId, ping, customData)`: set player's `ping`. host-only.
    - `[newPing, customData] = modifyClientPingBefore(ping)`: prepares a custom data object to send to all plugins while setting current player's `ping`. `customData=false` means "don't call callbacks". client-only.
    - `newPing = modifyClientPing(ping, customData)`: set current player's `ping`. client-only.
    - `newPing = modifyClientPingAfter(ping, customData)`: set current player's `ping`. client-only.
    - `[newFrameNo, customData] = modifyFrameNoBefore(frameNo)`: prepares a custom data object to send to all plugins while setting current player's `frameNo`. `customData=false` means "don't call callbacks". causes your player to look laggy to your opponents, especially on extrapolated clients. client-only.
    - `newFrameNo = modifyFrameNo(frameNo)`: set current player's `frameNo`. causes your player to look laggy to your opponents, especially on extrapolated clients. client-only.
    - `newFrameNo = modifyFrameNoAfter(frameNo, customData)`: set current player's `frameNo`. causes your player to look laggy to your opponents, especially on extrapolated clients. client-only.
    - `customData = onBeforeOperationReceived(type, msg, globalFrameNo, clientFrameNo)`: the host callback that is called only once for each message received from clients, and its return value is passed as customData to onOperationReceived callback. this callback is useful for parsing chat messages and other stuff that you would like to do only once, before the room callback or any plugin callbacks are called. The default callback value is a function that parses a chat message and returns `{ isCommand: boolean, data: string array }` where `isCommand = text.startsWith("!")` and `data = text.trimEnd().split(" ")`. 
    - `acceptEvent = onOperationReceived(type, msg, globalFrameNo, clientFrameNo, customData)`: runs for each message received from clients. `type` is the type of the operation, `msg` is the original message, `customData` is the return value of callback `onBeforeOperationReceived(type, msg, globalFrameNo, clientFrameNo)`. `onOperationReceived` is called only once for each message, before all `onOperationReceived` callbacks of all plugins are called for the same message. you may modify msg's contents here as you wish. `return true` -> accept event, `return false` -> block message from being processed, `throw exception` -> break message sender player's connection. host-only.
    - `acceptEvent = onAfterOperationReceived(type, msg, globalFrameNo, clientFrameNo, customData)`: runs for each message received from clients. `type` is the type of the operation, `msg` is the original message, `customData` is the return value of callback `onOperationReceived(type, globalFrameNo, clientFrameNo, msg)`. `onAfterOperationReceived` is called only once for each message, after all `onOperationReceived` callbacks of all plugins are called for the same message. you may modify msg's contents here as you wish. `return true` -> accept event, `return false` -> block message from being processed, `throw exception` -> break message sender player's connection. host-only.

  - `callbacks`:
    - `initialize(room)`: only called once while creating or joining a room, or during a call to `Room.setConfig`.
    - `finalize()`: only called once while leaving a room, or during a call to `Room.setConfig`.
    - `customData = onBeforeXXXXXXX(...)`: (where `XXXXXXX` is the name of the event) called before plugin callbacks. return a `customData` object to be used for each `plugin.onXXXXXXX(..., customData)` and then `room.onAfterXXXXXXX(..., customData)`. return `false` to stop propagation. 
    - `onXXXXXXX(..., customData)`: (where `XXXXXXX` is the name of the event) called after plugin callbacks, just before renderer callback. the last parameter, `customData`, is the data object that was returned from `room.onBeforeXXXXXXX(...)`.
    - `onAfterXXXXXXX(..., customData)`: (where `XXXXXXX` is the name of the event) called after renderer callback. the last parameter, `customData`, is the data object that was returned from `room.onXXXXXXX(...)`.
      - `customData = onBeforeRoomLink(link)`: room `link` was received. host-only.
      - `onRoomLink(link, customData)`: room `link` was received. host-only.
      - `onAfterRoomLink(link, customData)`: room `link` was received. host-only.
      - `customData = onBeforePlayerBallKick(playerId)`: ball was kicked by player(`playerId`). triggered individually.
      - `onPlayerBallKick(playerId, customData)`: ball was kicked by player(`playerId`). triggered individually.
      - `onAfterPlayerBallKick(playerId, customData)`: ball was kicked by player(`playerId`). triggered individually.
      - `customData = onBeforeTeamGoal(teamId)`: goal was scored by team(`teamId`). triggered individually.
      - `onTeamGoal(teamId, customData)`: goal was scored by team(`teamId`). triggered individually.
      - `onAfterTeamGoal(teamId, customData)`: goal was scored by team(`teamId`). triggered individually.
      - `customData = onBeforeGameEnd(winningTeamId)`: game was won by team(`winningTeamId`). triggered individually.
      - `onGameEnd(winningTeamId, customData)`: game was won by team(`winningTeamId`). triggered individually.
      - `onAfterGameEnd(winningTeamId, customData)`: game was won by team(`winningTeamId`). triggered individually.
      - `customData = onBeforeGameTick()`: runs on each game tick. (lots of times per second) triggered individually.
      - `onGameTick(customData)`: runs on each game tick. (lots of times per second) triggered individually.
      - `onAfterGameTick(customData)`: runs on each game tick. (lots of times per second) triggered individually.
      - `customData = onBeforePlayerSyncChange(playerId, value)`: player(`playerId`)'s synchronized status has changed to (`value`).
      - `onPlayerSyncChange(playerId, value, customData)`: player(`playerId`)'s synchronized status has changed to (`value`).
      - `onAfterPlayerSyncChange(playerId, value, customData)`: player(`playerId`)'s synchronized status has changed to (`value`).
      - `customData = onBeforeAnnouncement(msg, color, style, sound)`: a message(`msg`) with properties(`color`, `style`, `sound`) was announced by the room host. may only be triggered by host.
      - `onAnnouncement(msg, color, style, sound, customData)`: a message(`msg`) with properties(`color`, `style`, `sound`) was announced by the room host. may only be triggered by host.
      - `onAfterAnnouncement(msg, color, style, sound, customData)`: a message(`msg`) with properties(`color`, `style`, `sound`) was announced by the room host. may only be triggered by host.
      - `customData = onBeforeAutoTeams(playerId1, teamId1, playerId2, teamId2, byId)`: "auto" button was used by player(`byId`), it caused player(`playerId1`) to join team(`teamId1`) and player(`playerId2`) to join team(`teamId2`).
      - `onAutoTeams(playerId1, teamId1, playerId2, teamId2, byId, customData)`: "auto" button was used by player(`byId`), it caused player(`playerId1`) to join team(`teamId1`) and player(`playerId2`) to join team(`teamId2`).
      - `onAfterAutoTeams(playerId1, teamId1, playerId2, teamId2, byId, customData)`: "auto" button was used by player(`byId`), it caused player(`playerId1`) to join team(`teamId1`) and player(`playerId2`) to join team(`teamId2`).
      - `customData = onBeforeScoreLimitChange(value, byId)`: score limit was changed to (`value`) by player(`byId`).
      - `onScoreLimitChange(value, byId, customData)`: score limit was changed to (`value`) by player(`byId`).
      - `onAfterScoreLimitChange(value, byId, customData)`: score limit was changed to (`value`) by player(`byId`).
      - `customData = onBeforeTimeLimitChange(value, byId)`: time limit was changed to (`value`) by player(`byId`).
      - `onTimeLimitChange(value, byId, customData)`: time limit was changed to (`value`) by player(`byId`).
      - `onAfterTimeLimitChange(value, byId, customData)`: time limit was changed to (`value`) by player(`byId`).
      - `customData = onBeforePlayerAdminChange(id, isAdmin, byId)`: player(`id`)'s admin status was changed to (`isAdmin`) by player(`byId`).
      - `onPlayerAdminChange(id, isAdmin, byId, customData)`: player(`id`)'s admin status was changed to (`isAdmin`) by player(`byId`).
      - `onAfterPlayerAdminChange(id, isAdmin, byId, customData)`: player(`id`)'s admin status was changed to (`isAdmin`) by player(`byId`).
      - `customData = onBeforePlayerAvatarChange(id, value)`: player(`id`) changed its avatar to (`value`).
      - `onPlayerAvatarChange(id, value, customData)`: player(`id`) changed its avatar to (`value`).
      - `onAfterPlayerAvatarChange(id, value, customData)`: player(`id`) changed its avatar to (`value`).
      - `customData = onBeforePlayerHeadlessAvatarChange(id, value)`: player(`id`) changed its headless avatar to (`value`). may only be triggered by host.
      - `onPlayerHeadlessAvatarChange(id, value, customData)`: player(`id`) changed its headless avatar to (`value`). may only be triggered by host.
      - `onAfterPlayerHeadlessAvatarChange(id, value, customData)`: player(`id`) changed its headless avatar to (`value`). may only be triggered by host.
      - `customData = onBeforePlayersOrderChange(idList, moveToTop)`: players(`idList`) were removed, reordered to match the order in `idList` and added back to the (top or bottom)(`moveToTop`) of the player list. may only be triggered by host.
      - `onPlayersOrderChange(idList, moveToTop, customData)`: players(`idList`) were removed, reordered to match the order in `idList` and added back to the (top or bottom)(`moveToTop`) of the player list. may only be triggered by host.
      - `onAfterPlayersOrderChange(idList, moveToTop, customData)`: players(`idList`) were removed, reordered to match the order in `idList` and added back to the (top or bottom)(`moveToTop`) of the player list. may only be triggered by host.
      - `customData = onBeforePlayerTeamChange(id, teamId, byId)`: player(`id`) was moved to team(`teamId`) by player(`byId`).
      - `onPlayerTeamChange(id, teamId, byId, customData)`: player(`id`) was moved to team(`teamId`) by player(`byId`).
      - `onAfterPlayerTeamChange(id, teamId, byId, customData)`: player(`id`) was moved to team(`teamId`) by player(`byId`).
      - `customData = onBeforeStadiumChange(stadium, byId)`: room's current stadium was set to (`stadium`) by player(`byId`).
      - `onStadiumChange(stadium, byId, customData)`: room's current stadium was set to (`stadium`) by player(`byId`).
      - `onAfterStadiumChange(stadium, byId, customData)`: room's current stadium was set to (`stadium`) by player(`byId`).
      - `customData = onBeforeTeamsLockChange(value, byId)`: room's team lock status was set to (`value`) by player(`byId`).
      - `onTeamsLockChange(value, byId, customData)`: room's team lock status was set to (`value`) by player(`byId`).
      - `onAfterTeamsLockChange(value, byId, customData)`: room's team lock status was set to (`value`) by player(`byId`).
      - `customData = onBeforePlayerObjectCreated(playerObj)`: a player object(`playerObj`) was created.
      - `onPlayerObjectCreated(playerObj, customData)`: a player object(`playerObj`) was created.
      - `onAfterPlayerObjectCreated(playerObj, customData)`: a player object(`playerObj`) was created.
      - `customData = onBeforePlayerJoin(playerObj)`: a player(`playerObj`) joined the room.
      - `onPlayerJoin(playerObj, customData)`: a player(`playerObj`) joined the room.
      - `onAfterPlayerJoin(playerObj, customData)`: a player(`playerObj`) joined the room.
      - `customData = onBeforeGamePauseChange(isPaused, byId)`: room's game paused status was set to (`isPaused`) by player(`byId`).
      - `onGamePauseChange(isPaused, byId, customData)`: room's game paused status was set to (`isPaused`) by player(`byId`).
      - `onAfterGamePauseChange(isPaused, byId, customData)`: room's game paused status was set to (`isPaused`) by player(`byId`).
      - `customData = onBeforePlayerChat(id, message)`: a chat message with content(`message`) was received from player(`id`).
      - `onPlayerChat(id, message, customData)`: a chat message with content(`message`) was received from player(`id`).
      - `onAfterPlayerChat(id, message, customData)`: a chat message with content(`message`) was received from player(`id`).
      - `customData = onBeforePlayerInputChange(id, value)`: player(`id`)'s input has changed to (`value`).
      - `onPlayerInputChange(id, value, customData)`: player(`id`)'s input has changed to (`value`).
      - `onAfterPlayerInputChange(id, value, customData)`: player(`id`)'s input has changed to (`value`).
      - `customData = onBeforePlayerChatIndicatorChange(id, value)`: player(`id`)'s chat indicator status has changed to (`value`).
      - `onPlayerChatIndicatorChange(id, value, customData)`: player(`id`)'s chat indicator status has changed to (`value`).
      - `onAfterPlayerChatIndicatorChange(id, value, customData)`: player(`id`)'s chat indicator status has changed to (`value`).
      - `customData = onBeforePlayerLeave(playerObj, reason, isBanned, byId)`: player(`playerObj`) has left the room, (or was kicked or banned, i.e. `isBanned`) by player(`byId`) with reason(`reason`).
      - `onPlayerLeave(playerObj, reason, isBanned, byId, customData)`: player(`playerObj`) has left the room, (or was kicked or banned, i.e. `isBanned`) by player(`byId`) with reason(`reason`).
      - `onAfterPlayerLeave(playerObj, reason, isBanned, byId, customData)`: player(`playerObj`) has left the room, (or was kicked or banned, i.e. `isBanned`) by player(`byId`) with reason(`reason`).
      - `customData = onBeforeSetDiscProperties(id, type, data1, data2)`: (`type`=`0`: disc, `type`=`1`: player)(`id`)'s properties was set to (`data1`, `data2`). may only be triggered by host.
      - `onSetDiscProperties(id, type, data1, data2, customData)`: (`type`=`0`: disc, `type`=`1`: player)(`id`)'s properties was set to (`data1`, `data2`). may only be triggered by host.
      - `onAfterSetDiscProperties(id, type, data1, data2, customData)`: (`type`=`0`: disc, `type`=`1`: player)(`id`)'s properties was set to (`data1`, `data2`). may only be triggered by host.
      - `customData = onBeforeTeamColorsChange(teamId, value, byId)`: team(`teamId`)'s colors were changed to (`value`) by player(`byId`).
      - `onTeamColorsChange(teamId, value, byId, customData)`: team(`teamId`)'s colors were changed to (`value`) by player(`byId`).
      - `onAfterTeamColorsChange(teamId, value, byId, customData)`: team(`teamId`)'s colors were changed to (`value`) by player(`byId`).
      - `customData = onBeforeKickRateLimitChange(min, rate, burst, byId)`: room's kick rate limit was set to (`min`, `rate`, `burst`) by player(`byId`).
      - `onKickRateLimitChange(min, rate, burst, byId, customData)`: room's kick rate limit was set to (`min`, `rate`, `burst`) by player(`byId`).
      - `onAfterKickRateLimitChange(min, rate, burst, byId, customData)`: room's kick rate limit was set to (`min`, `rate`, `burst`) by player(`byId`).
      - `customData = onBeforeGameStart(byId)`: game was started by player(`byId`).
      - `onGameStart(byId, customData)`: game was started by player(`byId`).
      - `onAfterGameStart(byId, customData)`: game was started by player(`byId`).
      - `customData = onBeforeKickOff()`: game kicked off. triggered individually.
      - `onKickOff(customData)`: game kicked off. triggered individually.
      - `onAfterKickOff(customData)`: game kicked off. triggered individually.
      - `customData = onBeforeTimeIsUp()`: time is up. triggered individually.
      - `onTimeIsUp(customData)`: time is up. triggered individually.
      - `onAfterTimeIsUp(customData)`: time is up. triggered individually.
      - `customData = onBeforePositionsReset()`: positions were reset just after a goal. triggered individually.
      - `onPositionsReset(customData)`: positions were reset just after a goal. triggered individually.
      - `onAfterPositionsReset(customData)`: positions were reset just after a goal. triggered individually.
      - `customData = onBeforeLocalFrame(localFrameNo, customData)`: new game frame was received. triggered individually.
      - `onLocalFrame(localFrameNo, customData)`: new game frame was received. triggered individually.
      - `onAfterLocalFrame(localFrameNo, customData)`: new game frame was received. triggered individually.
      - `customData = onBeforeGameStop(byId)`: game was stopped by player(`byId`).
      - `onGameStop(byId, customData)`: game was stopped by player(`byId`).
      - `onAfterGameStop(byId, customData)`: game was stopped by player(`byId`).
      - `customData = onBeforePingData(array)`: ping values for all players was received. may only be triggered by host.
      - `onPingData(array, customData)`: ping values for all players was received. may only be triggered by host.
      - `onAfterPingData(array, customData)`: ping values for all players was received. may only be triggered by host.
      - `customData = onBeforeExtrapolationChange(value)`: extrapolation was set to (`value`). triggered individually.
      - `onExtrapolationChange(value, customData)`: extrapolation was set to (`value`). triggered individually.
      - `onAfterExtrapolationChange(value, customData)`: extrapolation was set to (`value`). triggered individually.
      - `customData = onBeforeHandicapChange(value)`: handicap was set to (`value`). triggered individually.
      - `onHandicapChange(value, customData)`: handicap was set to (`value`). triggered individually.
      - `onAfterHandicapChange(value, customData)`: handicap was set to (`value`). triggered individually.
      - `customData = onBeforeBansClear()`: all bans were cleared. host-only.
      - `onBansClear(customData)`: all bans were cleared. host-only.
      - `onAfterBansClear(customData)`: all bans were cleared. host-only.
      - `customData = onBeforeRoomRecaptchaModeChange(on)`: room's recaptcha mode was set to (`on`). host-only.
      - `onRoomRecaptchaModeChange(on, customData)`: room's recaptcha mode was set to (`on`). host-only.
      - `onAfterRoomRecaptchaModeChange(on, customData)`: room's recaptcha mode was set to (`on`). host-only.
      - `customData = onBeforeRoomRecordingChange(value)`: recording started(`value`=`true`) or stopped(`value` is `arraybuffer`). triggered individually.
      - `onRoomRecordingChange(value, customData)`: recording started(`value`=`true`) or stopped(`value` is `arraybuffer`). triggered individually.
      - `onAfterRoomRecordingChange(value, customData)`: recording started(`value`=`true`) or stopped(`value` is `arraybuffer`). triggered individually.
      - `customData = onBeforeRoomPropertiesChange(props)`: room's properties(`props`) were changed. host-only.
      - `onRoomPropertiesChange(props, customData)`: room's properties(`props`) were changed. host-only.
      - `onAfterRoomPropertiesChange(props, customData)`: room's properties(`props`) were changed. host-only.
      - `customData = onBeforeCollisionDiscVsDisc(discId1, discPlayerId1, discId2, discPlayerId2)`: a collision happened between disc(`discId1`, `playerId1`) and disc(`discId2`, `playerId2`). triggered individually.
      - `onCollisionDiscVsDisc(discId1, discPlayerId1, discId2, discPlayerId2, customData)`: a collision happened between disc(`discId1`, `playerId1`) and disc(`discId2`, `playerId2`). triggered individually.
      - `onAfterCollisionDiscVsDisc(discId1, discPlayerId1, discId2, discPlayerId2, customData)`: a collision happened between disc(`discId1`, `playerId1`) and disc(`discId2`, `playerId2`). triggered individually.
      - `customData = onBeforeCollisionDiscVsSegment(discId, discPlayerId, segmentId)`: a collision happened between disc(`discId`, `discPlayerId`) and segment(`segmentId`). triggered individually.
      - `onCollisionDiscVsSegment(discId, discPlayerId, segmentId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and segment(`segmentId`). triggered individually.
      - `onAfterCollisionDiscVsSegment(discId, discPlayerId, segmentId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and segment(`segmentId`). triggered individually.
      - `customData = onBeforeCollisionDiscVsPlane(discId, discPlayerId, planeId)`: a collision happened between disc(`discId`, `discPlayerId`) and plane(`planeId`). triggered individually.
      - `onCollisionDiscVsPlane(discId, discPlayerId, planeId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and plane(`planeId`). triggered individually.
      - `onAfterCollisionDiscVsPlane(discId, discPlayerId, planeId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and plane(`planeId`). triggered individually.
      - `customData = onBeforeCustomEvent(type, data, byId)`: a custom event(`type`, `data`) was triggered by player(`byId`). custom-(host,client)s-only.
      - `onCustomEvent(type, data, byId, customData)`: a custom event(`type`, `data`) was triggered by player(`byId`). custom-(host,client)s-only.
      - `onAfterCustomEvent(type, data, byId, customData)`: a custom event(`type`, `data`) was triggered by player(`byId`). custom-(host,client)s-only.
      - `customData = onBeforePluginActiveChange(plugin)`: a `plugin` was activated/deactivated. triggered individually.
      - `onPluginActiveChange(plugin, customData)`: a `plugin` was activated/deactivated. triggered individually.
      - `onAfterPluginActiveChange(plugin, customData)`: a `plugin` was activated/deactivated. triggered individually.
      - `customData = onBeforeConfigUpdate(oldRoomConfigObj, newRoomConfigObj)`: an old roomConfig object(`oldRoomConfigObj`) was replaced by a new roomConfig object(`newRoomConfigObj`).
      - `onConfigUpdate(oldRoomConfigObj, newRoomConfigObj, customData)`: an old roomConfig object(`oldRoomConfigObj`) was replaced by a new roomConfig object(`newRoomConfigObj`).
      - `onAfterConfigUpdate(oldRoomConfigObj, newRoomConfigObj, customData)`: an old roomConfig object(`oldRoomConfigObj`) was replaced by a new roomConfig object(`newRoomConfigObj`).
      - `customData = onBeforeRendererUpdate(oldRendererObj, newRendererObj)`: an old renderer object(`oldRendererObj`) was replaced by a new renderer object(`newRendererObj`).
      - `onRendererUpdate(oldRendererObj, newRendererObj, customData)`: an old renderer object(`oldRendererObj`) was replaced by a new renderer object(`newRendererObj`).
      - `onAfterRendererUpdate(oldRendererObj, newRendererObj, customData)`: an old renderer object(`oldRendererObj`) was replaced by a new renderer object(`newRendererObj`).
      - `customData = onBeforePluginUpdate(oldPluginObj, newPluginObj)`: an old plugin object(`oldPluginObj`) was replaced by a new plugin object(`newPluginObj`).
      - `onPluginUpdate(oldPluginObj, newPluginObj, customData)`: an old plugin object(`oldPluginObj`) was replaced by a new plugin object(`newPluginObj`).
      - `onAfterPluginUpdate(oldPluginObj, newPluginObj, customData)`: an old plugin object(`oldPluginObj`) was replaced by a new plugin object(`newPluginObj`).
      - `customData = onBeforeLanguageChange(abbr)`: API's language abbreviation was changed to `abbr`.
      - `onLanguageChange(abbr, customData)`: API's language abbreviation was changed to `abbr`.
      - `onAfterLanguageChange(abbr, customData)`: API's language abbreviation was changed to `abbr`.

- `Plugin`: A class that defines a plugin. Any plugin should be based on this class.

  - `constructor(name, active, metadata)`: creates a new Plugin instance. A plugin is automatically activated just after initialization, while a Room object is being created, if active is true. Metadata is the information that you would want to show/update inside a GUI application.

  - `properties`:
    - `name`: name of the plugin. Must be unique, and is used internally in `Room.setPluginActive`. All Plugins can be accessed with their names via `Room.pluginsMap[name]`.
    - `active`: activation status of the plugin. You should use `Room.setPluginActive(name, active)` if you want to modify this value manually.

  - `abstract callbacks`: These functions should be overridden when writing a GUI application using this API before creating any `Plugin` object. These are defined in `Plugin.prototype`.
    - `defineMetadata(metadata)`: Does nothing, returns nothing by default. This function should define the given `metadata` object inside this `Plugin` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the plugins in the examples folder use the following metadata structure: `{version, author, description, allowFlags}`.
    - `defineVariable(variable)`: Does nothing, returns `variable`'s value by default. This function should define the given `variable` object inside this `Plugin` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the plugins in the examples folder use the following variable structure: `{name, type, value, range, description}`. This function should return the value of the `variable` since it is used once in the constructor for the plugin's `active` property. This function should be used whenever a variable whose value is changeable from outside will be defined. 

  - `modifier callbacks`:
    - `[modifiedName, modifiedFlag, modifiedAvatar] = modifyPlayerData(playerId, name, flag, avatar, conn, auth, customData)`: set player's data just before player has joined the room. `return null` -> player is not allowed to join. `customData` is an optional data object returned from `room.modifyPlayerDataBefore`. host-only.
    - `newPing = modifyPlayerPing(playerId, ping, customData)`: set player's `ping`. `customData` is an optional data object returned from `room.modifyPlayerPingBefore`. host-only.
    - `newPing = modifyClientPing(ping, customData)`: set current player's `ping`. `customData` is an optional data object returned from `room.modifyClientPingBefore`. client-only.
    - `newFrameNo = modifyFrameNo(frameNo, customData)`: set current player's `frameNo`. causes your player to look laggy to your opponents, especially on extrapolated clients. `customData` is an optional data object returned from `room.modifyFrameNoBefore`. client-only.
    - `acceptEvent = onOperationReceived(type, msg, globalFrameNo, clientFrameNo, customData)`:  runs for each message received from clients. `type` is the type of the operation, `msg` is the original message. you may modify `msg`'s contents here as you wish. `customData` is an optional data object returned from `room.onBeforeOperationReceived`. `return true` -> accept event, `return false` -> block message from being processed, `throw exception` -> break message sender player's connection. host-only.

  - `callbacks`:
    - `initialize(room)`: only called once while creating or joining a room, or during a call to `Room.updatePlugin`.
    - `finalize()`: only called once while leaving a room, or during a call to `Room.updatePlugin`.
    - `onXXXXXXX(..., customData)`: (where `XXXXXXX` is the name of the event) called after `room.onBeforeXXXXXXX(...)` and before `room.onAfterXXXXXXX(..., customData)`. `customData` is the object that might be returned from `room.onBeforeXXXXXXX(...)`.
      - `onRoomLink(link, customData)`: room link was received. host-only.
      - `onPlayerBallKick(playerId, customData)`: ball was kicked by player(`playerId`). triggered individually.
      - `onTeamGoal(teamId, customData)`: goal was scored by team(`teamId`). triggered individually.
      - `onGameEnd(winningTeamId, customData)`: game was won by team(`winningTeamId`). triggered individually.
      - `onGameTick(customData)`: runs on each game tick. (lots of times per second) triggered individually.
      - `onPlayerSyncChange(playerId, value, customData)`: player(`playerId`)'s synchronized status has changed to (`value`).
      - `onAnnouncement(msg, color, style, sound, customData)`: a message(`msg`) with properties(`color`, `style`, `sound`) was announced by the room host. may only be triggered by host.
      - `onAutoTeams(playerId1, teamId1, playerId2, teamId2, byId, customData)`: "auto" button was used by player(`byId`), it caused player(`playerId1`) to join team(`teamId1`) and player(`playerId2`) to join team(`teamId2`).
      - `onScoreLimitChange(value, byId, customData)`: score limit was changed to (`value`) by player(`byId`).
      - `onTimeLimitChange(value, byId, customData)`: time limit was changed to (`value`) by player(`byId`).
      - `onPlayerAdminChange(id, isAdmin, byId, customData)`: player(`id`)'s admin status was changed to (`isAdmin`) by player(`byId`).
      - `onPlayerAvatarChange(id, value, customData)`: player(`id`) changed its avatar to (`value`).
      - `onPlayerHeadlessAvatarChange(id, value, customData)`: player(`id`) changed its headless avatar to (`value`). may only be triggered by host.
      - `onPlayersOrderChange(idList, moveToTop, customData)`: players(`idList`) were removed, reordered to match the order in `idList` and added back to the (top or bottom)(`moveToTop`) of the player list. may only be triggered by host.
      - `onPlayerTeamChange(id, teamId, byId, customData)`: player(`id`) was moved to team(`teamId`) by player(`byId`).
      - `onStadiumChange(stadium, byId, customData)`: room's current stadium was set to (`stadium`) by player(`byId`).
      - `onTeamsLockChange(value, byId, customData)`: room's team lock status was set to (`value`) by player(`byId`).
      - `onPlayerObjectCreated(playerObj, customData)`: a player object(`playerObj`) was created.
      - `onPlayerJoin(playerObj, customData)`: a player(`playerObj`) joined the room.
      - `onGamePauseChange(isPaused, byId, customData)`: room's game paused status was set to (`isPaused`) by player(`byId`).
      - `onPlayerChat(id, message, customData)`: a chat message with content(`message`) was received from player(`id`).
      - `onPlayerInputChange(id, value, customData)`: player(`id`)'s input has changed to (`value`).
      - `onPlayerChatIndicatorChange(id, value, customData)`: player(`id`)'s chat indicator status has changed to (`value`).
      - `onPlayerLeave(playerObj, reason, isBanned, byId, customData)`: player(`playerObj`) has left the room (or was kicked or banned, i.e. `isBanned`) by player(`byId`) with reason(`reason`).
      - `onSetDiscProperties(id, type, data1, data2, customData)`: (`type`=`0`: disc, `type`=`1`: player)(`id`)'s properties was set to (`data1`, `data2`). may only be triggered by host.
      - `onTeamColorsChange(teamId, value, byId, customData)`: team(`teamId`)'s colors were changed to (`value`) by player(`byId`).
      - `onKickRateLimitChange(min, rate, burst, byId, customData)`: room's kick rate limit was set to (`min`, `rate`, `burst`) by player(`byId`).
      - `onGameStart(byId, customData)`: game was started by player(`byId`).
      - `onKickOff(customData)`: game kicked off. triggered individually.
      - `onTimeIsUp(customData)`: time is up. triggered individually.
      - `onPositionsReset(customData)`: positions were reset just after a goal. triggered individually.
      - `onLocalFrame(localFrameNo, customData)`: new game frame was received. triggered individually.
      - `onGameStop(byId, customData)`: game was stopped by player(`byId`).
      - `onPingData(array, customData)`: ping values for all players was received. may only be triggered by host.
      - `onExtrapolationChange(value, customData)`: extrapolation was set to (`value`). triggered individually.
      - `onHandicapChange(value, customData)`: handicap was set to (`value`). triggered individually.
      - `onBansClear(customData)`: all bans were cleared. host-only.
      - `onRoomRecaptchaModeChange(on, customData)`: room's recaptcha mode was set to (`on`). host-only.
      - `onRoomRecordingChange(value, customData)`: recording started(`value`=`true`) or stopped(`value` is `arraybuffer`). triggered individually.
      - `onRoomPropertiesChange(props, customData)`: room's properties(`props`) were changed. host-only.
      - `onCollisionDiscVsDisc(discId1, discPlayerId1, discId2, discPlayerId2, customData)`: a collision happened between disc(`discId1`, `playerId1`) and disc(`discId2`, `playerId2`). triggered individually.
      - `onCollisionDiscVsSegment(discId, discPlayerId, segmentId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and segment(`segmentId`). triggered individually.
      - `onCollisionDiscVsPlane(discId, discPlayerId, planeId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and plane(`planeId`). triggered individually.
      - `onCustomEvent(type, data, byId, customData)`: a custom event(`type`, `data`) was triggered by player(`byId`). custom-(host,client)s-only.
      - `onPluginActiveChange(plugin, customData)`: a plugin was activated/deactivated. triggered individually.
      - `onConfigUpdate(oldRoomConfigObj, newRoomConfigObj, customData)`: an old roomConfig object(`oldRoomConfigObj`) was replaced by a new roomConfig object(`newRoomConfigObj`).
      - `onRendererUpdate(oldRendererObj, newRendererObj, customData)`: an old renderer object(`oldRendererObj`) was replaced by a new renderer object(`newRendererObj`).
      - `onPluginUpdate(oldPluginObj, newPluginObj, customData)`: an old plugin object(`oldPluginObj`) was replaced by a new plugin object(`newPluginObj`).
      - `onLanguageChange(abbr, customData)`: API's language abbreviation was changed to `abbr`.

- `Renderer`: A class that defines a renderer. Any renderer should be based on this class.

  - `constructor(metadata)`: creates a new `Renderer` instance. `metadata` is the information that you would want to show/update inside a GUI application.

  - `abstract callbacks`: These functions should be overridden when writing a GUI application using this API before creating any `Renderer` object. These are defined in `Renderer.prototype`.
    - `defineMetadata(metadata)`: Does nothing, returns nothing by default. This function should define the given `metadata` object inside this `Renderer` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the default renderer in the examples folder uses the following `metadata` structure: `{name, version, author, description}`.
    - `defineVariable(variable)`: Does nothing, returns `variable`'s value by default. This function should define the given `variable` object inside this `Renderer` object. This is not done here for optimization purposes. (We do not need these values in a non-GUI environment.) For example, the default renderer in the examples folder use the following variable structure: `{name, type, value, range, description}`. This function should return the value of the `variable`, and should be used whenever a variable whose value is changeable from outside will be defined. 

  - `callbacks`:
    - `initialize(room)`: only called once while creating or joining a room, or during a call to `Room.setRenderer`.
    - `finalize()`: only called once while leaving a room, or during a call to `Room.setRenderer`.
    - `render(extrapolatedRoomState)`: called inside `requestAnimationFrame` callback. rendering logic should be here. 
    - `onXXXXXXX(..., customData)`: (where `XXXXXXX` is the name of the event) called after the respective plugin callbacks `plugin.onXXXXXXX(...)` and `room.onXXXXXXX(..., customData)`. `customData` is the object that might be returned from the last call of `plugin.onXXXXXXX(...)` or `room.onXXXXXXX(...)`.
      - `onRoomLink(link, customData)`: room link was received. host-only.
      - `onPlayerBallKick(playerId, customData)`: ball was kicked by player(`playerId`). triggered individually.
      - `onTeamGoal(teamId, customData)`: goal was scored by team(`teamId`). triggered individually.
      - `onGameEnd(winningTeamId, customData)`: game was won by team(`winningTeamId`). triggered individually.
      - `onGameTick(customData)`: runs on each game tick. (lots of times per second) triggered individually.
      - `onPlayerSyncChange(playerId, value, customData)`: player(`playerId`)'s synchronized status has changed to (`value`).
      - `onAnnouncement(msg, color, style, sound, customData)`: a message(`msg`) with properties(`color`, `style`, `sound`) was announced by the room host. may only be triggered by host.
      - `onAutoTeams(playerId1, teamId1, playerId2, teamId2, byId, customData)`: "auto" button was used by player(`byId`), it caused player(`playerId1`) to join team(`teamId1`) and player(`playerId2`) to join team(`teamId2`).
      - `onScoreLimitChange(value, byId, customData)`: score limit was changed to (`value`) by player(`byId`).
      - `onTimeLimitChange(value, byId, customData)`: time limit was changed to (`value`) by player(`byId`).
      - `onPlayerAdminChange(id, isAdmin, byId, customData)`: player(`id`)'s admin status was changed to (`isAdmin`) by player(`byId`).
      - `onPlayerAvatarChange(id, value, customData)`: player(`id`) changed its avatar to (`value`).
      - `onPlayerHeadlessAvatarChange(id, value, customData)`: player(`id`) changed its headless avatar to (`value`). may only be triggered by host.
      - `onPlayersOrderChange(idList, moveToTop, customData)`: players(`idList`) were removed, reordered to match the order in `idList` and added back to the (top or bottom)(`moveToTop`) of the player list. may only be triggered by host.
      - `onPlayerTeamChange(id, teamId, byId, customData)`: player(`id`) was moved to team(`teamId`) by player(`byId`).
      - `onStadiumChange(stadium, byId, customData)`: room's current stadium was set to (`stadium`) by player(`byId`).
      - `onTeamsLockChange(value, byId, customData)`: room's team lock status was set to (`value`) by player(`byId`).
      - `onPlayerObjectCreated(playerObj, customData)`: a player object(`playerObj`) was created.
      - `onPlayerJoin(playerObj, customData)`: a player(`playerObj`) joined the room.
      - `onGamePauseChange(isPaused, byId, customData)`: room's game paused status was set to (`isPaused`) by player(`byId`).
      - `onPlayerChat(id, message, customData)`: a chat message with content(`message`) was received from player(`id`).
      - `onPlayerInputChange(id, value, customData)`: player(`id`)'s input has changed to (`value`).
      - `onPlayerChatIndicatorChange(id, value, customData)`: player(`id`)'s chat indicator status has changed to (`value`).
      - `onPlayerLeave(playerObj, reason, isBanned, byId, customData)`: player(`playerObj`) has left the room (or was kicked or banned, i.e. `isBanned`) by player(`byId`) with reason(`reason`).
      - `onSetDiscProperties(id, type, data1, data2, customData)`: (`type`=`0`: disc, `type`=`1`: player)(`id`)'s properties was set to (`data1`, `data2`). may only be triggered by host.
      - `onKickRateLimitChange(min, rate, burst, byId, customData)`: room's kick rate limit was set to (`min`, `rate`, `burst`) by player(`byId`).
      - `onTeamColorsChange(teamId, value, byId, customData)`: team(`teamId`)'s colors were changed to (`value`) by player(`byId`).
      - `onGameStart(byId, customData)`: game was started by player(`byId`).
      - `onKickOff(customData)`: game kicked off. triggered individually.
      - `onTimeIsUp(customData)`: time is up. triggered individually.
      - `onPositionsReset(customData)`: positions were reset after a goal. triggered individually.
      - `onLocalFrame(localFrameNo, customData)`: new game frame was received. triggered individually.
      - `onGameStop(byId, customData)`: game was stopped by player(`byId`).
      - `onPingData(array, customData)`: ping values for all players was received. may only be triggered by host.
      - `onExtrapolationChange(value, customData)`: extrapolation was set to (`value`). triggered individually.
      - `onHandicapChange(value, customData)`: handicap was set to (`value`). triggered individually.
      - `onBansClear(customData)`: all bans were cleared. host-only.
      - `onRoomRecaptchaModeChange(on, customData)`: room's recaptcha mode was set to (`on`). host-only.
      - `onRoomRecordingChange(value, customData)`: recording started(`value`=`true`) or stopped(`value` is `ArrayBuffer`). triggered individually.
      - `onRoomPropertiesChange(props, customData)`: room's properties(`props`) were changed. host-only.
      - `onCollisionDiscVsDisc(discId1, discPlayerId1, discId2, discPlayerId2, customData)`: a collision happened between disc(`discId1`, `playerId1`) and disc(`discId2`, `playerId2`). triggered individually.
      - `onCollisionDiscVsSegment(discId, discPlayerId, segmentId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and segment(`segmentId`). triggered individually.
      - `onCollisionDiscVsPlane(discId, discPlayerId, planeId, customData)`: a collision happened between disc(`discId`, `discPlayerId`) and plane(`planeId`). triggered individually.
      - `onCustomEvent(type, data, byId, customData)`: a custom event(`type`, `data`) was triggered by player(`byId`). custom-(host,client)s-only.
      - `onPluginActiveChange(plugin, customData)`: a plugin was activated/deactivated. triggered individually.
      - `onConfigUpdate(oldRoomConfigObj, newRoomConfigObj, customData)`: an old roomConfig object(`oldRoomConfigObj`) was replaced by a new roomConfig object(`newRoomConfigObj`).
      - `onRendererUpdate(oldRendererObj, newRendererObj, customData)`: an old renderer object(`oldRendererObj`) was replaced by a new renderer object(`newRendererObj`).
      - `onPluginUpdate(oldPluginObj, newPluginObj, customData)`: an old plugin object(`oldPluginObj`) was replaced by a new plugin object(`newPluginObj`).
      - `onLanguageChange(abbr, customData)`: API's language abbreviation was changed to `abbr`.

- `Impl`: Implementation of Haxball's inner classes. All important classes are exported and more detailed explanations will hopefully be available soon. Names might be fixed later. These classes are enough to run your own Haxball website.

  - `Core`: Most important core classes used inside Haxball.
    - `H`: Point class
    - `ka`: TeamColors class
    - `p`: Team class
    - `T`: GeoLocation class

  - `Stream`: These classes are used to read/write data from/to replay files and/or network/WebRTC stream.
    - `F`: StreamReader class
    - `w`: StreamWriter class

  - `Utils`: Some utility classes (all of them may not be necessarily useful but still, why not export them?)
    - `U`: string operations 1
    - `D`: string operations 2
    - `J`: string operations 3
    - `K`: string operations 4
    - `r`: mostly used for object casting
    - `M`: webserver api operations
    - `n`: connection constants
    - `va`: RoomList operations
    - `q`: global error class


[Back To The Top](#title)

---

<h2 id="how-to-contribute">💡 How To Contribute</h2>

- Make a fork of this repository
- Clone to you machine and entry on respective paste
- Create a branch with your resource: `git checkout -b my-feature`
- Commit your changes: `git commit -m 'feat: My new feature'`
- Push your branch: `git push origin my-feature`
- A green button will appear at the beginning of this repository
- Click to open and fill in the pull request information

<p align="center">
<i>Contributions, issues and features requests are welcome!</i><br />
<i>📮 Submit PRs to help solve issues or add features</i><br />
<i>🐛 Find and report issues</i><br />
<i>🌟 Star the project</i><br />
</p>

[Back To The Top](#title)

---

<h2 id="contributors">🤗 Contributors</h2>

<p>

<div> - Initial testing environment by <a href="https://github.com/mertushka">mertushka <img width="20" src="https://avatars1.githubusercontent.com/u/34413473?v=4"/></a></div>
<div> - %99 of the bot API features by <a href="https://github.com/wxyz-abcd">abc <img width="20" src="https://avatars1.githubusercontent.com/u/8694183?v=4"/></a></div>
<div> - Room.modifyFrameNo by <a href="https://github.com/hxgd1">Punisher <img width="20" src="https://avatars.githubusercontent.com/u/114198188?v=4"/></a></div>
<div> - Autoplay bot examples improved by <a href="https://github.com/K0nfy">K0nfy <img width="20" src="https://avatars.githubusercontent.com/u/27099419?v=4"/></a></div>
<div> - Rest of the features by <a href="https://github.com/0x00214131812049">0x00 <img width="20" src="https://avatars.githubusercontent.com/u/96322566?v=4"/></a></div>
<div> - Docs formatted by <a href="https://github.com/uzayyli">uzaylı <img width="20" src="https://avatars.githubusercontent.com/u/87779551?v=4"/></a></div>
<div></div>
<div>We will continue to add all contributors to this list.</div>

</p>

[Back To The Top](#title)

---

<h2 id="license">🔏 License</h2>

MIT License, Copyright © 2022-2023 [abc](https://github.com/wxyz-abcd)

Absolutely no rights reserved. Do whatever you want with the codes. 

We do not take any responsibility on potential harm caused by this code. Use at your own risk, and be creative. :)

[Back To The Top](#title)
