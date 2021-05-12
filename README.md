# automerge-discovery

Manage multiple peers per document and sync over any connection

```
npm i automerge-discovery
```

## Usage

```js
import AutomergeDiscovery from 'automerge-discovery';

let doc = Automerge.init()

let manager = new AutomergeDiscovery(doc);

manager.on('patch', (patch) => {
  // Do something with the patch.
})

manager.on('sync', (peerId) => {
  console.log('Up to date with peer ', peerId)
})

```


For example, using this with Websockets:

```js
let socket = getWebsocketConnectionForDocument(doc)

// Messages are Uint8arrays
socket.binarytype = 'arraybuffer'

let receive = manager.addPeer(peerId, (msg) => {
  socket.send(msg)
})

socket.onmessage = (e) => {
  let msg = { e.data } 
  receive(msg)
}

```
