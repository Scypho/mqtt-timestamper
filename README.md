This is a small utility that adds timestamps to MQTT JSON messages

# Installation

    npm install --save mqtt-timestamper

# Usage

```javascript
var Timestamper = require('mqtt-timestamper');
var mqtt    = require('mqtt');
var client  = mqtt.connect('mqtt://test.mosquitto.org');

var timestamper = new Timestamper(client, 'sensors/#', function(topic) {
    return 'stamped/' + topic.slice('sensors/'.length);
}, {
    qos: 2
});

setTimeout(function() {
    timestamper.unsubscribe();
    timestamper.stop();
    client.end();
}, 1000);
```
