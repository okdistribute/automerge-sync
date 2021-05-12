# automerge-discovery

Manage multiple peers per document and sync over any connection

```
npm i automerge-discovery
```

## Usage

```js
let doc = Automerge.init()

let manager = new AutomergeDiscovery(doc);

manager.on('sync', (peerId) => {
  console.log('Up to date with peer ', peerId)
})

socket.binarytype = 'arraybuffer'

let receive = manager.addPeer(peerId, (msg) => {
  socket.send(msg)
})

socket.onmessage = (e) => {
  let msg = { e.data } 
  receive(msg)
}

```
