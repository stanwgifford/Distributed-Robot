# Distributed-Robot
This is a repository for the code for a MQTT swift (macOS) controlled robot

There is a swift project that uses CocoaMQTT - Robot
On the MAC I have created a Mosquitto server which is what everything talks to

There are currently two Raspberry Pi's for the disributed part.

A Pi Zero named Lidar controls a servo with a VL53LOX lidar mounted on it.
This on receipt of a MQTT command does a 180 degree scan at 5 degree intervals and sends the data back to the MQTT server.

A second Pi (Video) has a camera mounted on it. This on command takes a 640 * 480 image and sends it back to the MQTT Server 

The swift Application upon start up has a button connect - pushing this connects it to the MQTT Server

A second button called Enable starts everything up.

Via timers it sends a Lidar scan command every two seconds.

Currently a seperate button initiates the camera grab. Once pushed, it sends the camaer a command to grab an image.

The receive events in the swit program work as follows;

For the camera data, it displays the image and sends a request back to the camera for another image.

For the Lidar data it displays the data - a seperate time event fires to instruct the Lidar to scan.

A heartbeat mechanism is implimented to show the status of the various components. A heartbeat is sent every second. If a heartbeat has not been received in the last two seconds the heartbeat status for the component changes from Green to Yellow

