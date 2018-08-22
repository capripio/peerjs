# PeerJS: Simple peer-to-peer with WebRTC #

[![Backers on Open Collective](https://opencollective.com/peer/backers/badge.svg)](#backers)
 [![Sponsors on Open Collective](https://opencollective.com/peer/sponsors/badge.svg)](#sponsors) 

PeerJS provides a complete, configurable, and easy-to-use peer-to-peer API built on top of WebRTC, supporting both data channels and media streams.

### [http://peerjs.com](http://peerjs.com)

## Setup


**Include the library**

  with modules:
  `npm install https://github.com/capripio/peerjs/tarball/master`
    and the usage:
  ```js
  import Peer from 'peerjs';
  ```


**Create a Peer**  
Get a [free API key](http://peerjs.com/peerserver). Your id only needs to be unique to the namespace of your API key.
```javascript
var peer = new Peer('pick-an-id', {key: 'myapikey'}); 
// You can pick your own id or omit the id if you want to get a random one from the server.
```

## Data connections
**Connect**
```javascript
var conn = peer.connect('another-peers-id');
conn.on('open', function(){
  conn.send('hi!');
});
```
**Receive**
```javascript
peer.on('connection', function(conn) {
  conn.on('data', function(data){
    // Will print 'hi!'
    console.log(data);
  });
});
```

## Media calls
**Call**
```javascript
navigator.getUserMedia = navigator.getUserMedia || navigator.webkitGetUserMedia || navigator.mozGetUserMedia;
navigator.getUserMedia({video: true, audio: true}, function(stream) {
  var call = peer.call('another-peers-id', stream);
  call.on('stream', function(remoteStream) {
    // Show stream in some <video> element.
  });
}, function(err) {
  console.log('Failed to get local stream' ,err);
});

```
**Answer**
```javascript
navigator.getUserMedia = navigator.getUserMedia || navigator.webkitGetUserMedia || navigator.mozGetUserMedia;
peer.on('call', function(call) {
  navigator.getUserMedia({video: true, audio: true}, function(stream) {
    call.answer(stream); // Answer the call with an A/V stream.
    call.on('stream', function(remoteStream) {
      // Show stream in some <video> element.
    });
  }, function(err) {
    console.log('Failed to get local stream' ,err);
  });
});
```
## Links

### [Documentation / API Reference](http://peerjs.com/docs)

### [WebRTC Browser compatibility status](http://peerjs.com/status)

### [PeerServer](https://github.com/peers/peerjs-server)

### [Discuss PeerJS on our Google Group](https://groups.google.com/forum/?fromgroups#!forum/peerjs)

### [Changelog](https://github.com/peers/peerjs/blob/master/changelog.md)

## Contributors

This project exists thanks to all the people who contribute. [[Contribute](CONTRIBUTING.md)].
<a href="graphs/contributors"><img src="https://opencollective.com/peer/contributors.svg?width=890&button=false" /></a>

## Backers

Thank you to all our backers! [[Become a backer](https://opencollective.com/peer#backer)]

<a href="https://opencollective.com/peer#backers" target="_blank"><img src="https://opencollective.com/peer/backers.svg?width=890"></a>


## Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website. [[Become a sponsor](https://opencollective.com/peer#sponsor)]

<a href="https://opencollective.com/peer/sponsor/0/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/1/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/2/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/3/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/4/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/5/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/6/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/7/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/8/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/peer/sponsor/9/website" target="_blank"><img src="https://opencollective.com/peer/sponsor/9/avatar.svg"></a>



## License

PeerJS is licensed under the [MIT License](https://tldrlegal.com/l/mit).

