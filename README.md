# aliveim-service

Micro service that spawns Timer based objects and trigger a notification at timeout

# About alive.im

This service aims to solve a problem people may have with many connected devices or servers. Each device "pings" alive.im service just to tell it "Hey! I'm alive!". The service internally keep track of all these devices and their configuration, triggering a notification if the given device doesn't send an "I'm alive!" message in a given time frame. For example you can setup a RaspberryPi device to send an "I'm alive!" message every 1 minute and tell alive.im service to send you an email if it doesn't receive a message within 5 minutes. When the message is received, the timer is reset.

# About alive-im micro service

The micro service listens to an internal interface for a POST message sent by the main service. The main service will communicate the device ID (that will be used to identify the device in the timers pool) and the maximum timeout. Once received these informations, the micro service spawns a Timer based object with the device informations. If the device send another "ping" within the maximum timeout, the Timer is reset. If the timeout expires before receiving a new "ping" message, the notification is triggered.
