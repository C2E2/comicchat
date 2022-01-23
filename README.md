`<font face="ms comic sans">`

# comicchat

Quick and dirty. Based off Microsoft Comic Chat. Uses node.js and websockets.

![Screenshot](http://i.imgur.com/J1k7iwn.png)

# About this Fork

This is a scratch-pad to develop patches from a heavily modified version of gyng's Compic Chat for Node.  Please don't get attached to this fork.  Interesting improvements will be headed back upstream as soon as they are looking stable. -Corwin

## The C2E2 Project

C2E2 a rewrite of Comic Chat using ES5 classes focusing on scalability and introducing a concept of trusted connections using a private TLS socket introduced between the server and the IRC relay which enables additional messages types not directly avialable via the public websocket.   I'm not an heavy user of GH, but you can find such active development as I've managed to push over on my SourceHut, here:  https://sr.ht/~mplscorwin/C2E2/

## Features

* Comic chat
* Rooms
* Notifications
* Text-to-speech via Web Speech API
* Basic relay support for animating your (IRC) chat

## Usage

0. Clone repo.
1. `npm install` or `yarn install`
2. Change address of server in `client/js/client.js`, or supply it via a query param `http://example.com?server=ws://localhost:8084`
3. Change port of server in `server/server.js`
4. `node server/server.js` or `npm start`, args `--port 8084` (default), `--historySize 500` (default)
5. Visit `client/index.html`

## Deploy

* Deploy the client to `gh-pages` with `npm run deploy`

## Protocol

Connect to the WebSocket server and start pushing JSON. Subject to change.

### Send

    {
        type: 'join',
        room: 'room'
    }

* `history`, `join`, `part` require `room`
* `message` requires `room` and `text`, `spoof: true` optional for relays

### Receive

* `history` --- `type`, `history` (an array of messages for the requested room)
* `message` --- `type`, `room`, `time`, `text`, `author`

## Relay

If you want to watch your Best Internet IRC Friends in a voiced comic you can configure `relay/relay.js` and then run it with `node relay/relay.js`.

## TODO

* Tests

`</font>`
