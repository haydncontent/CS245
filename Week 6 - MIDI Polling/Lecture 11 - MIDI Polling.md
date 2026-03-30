PortMidi: polling mechanism
- holds input messages in a queue
- queue must be queried/polled to see there is one or more messages
- if there is a message, pull it off the queue
- to minimize latency, need to pull in a busy-wait loop in a separate thread