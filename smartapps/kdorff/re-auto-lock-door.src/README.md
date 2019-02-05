# Re-Auto Lock Door

I've been a long time user of  
["Enhanced Auto Lock Door"](https://github.com/SmartThingsCommunity/SmartThingsPublic/tree/master/smartapps/lock-auto-super-enhanced)
by Arnaud. This can be found in the SmartThings SmartApp Store under Safety & Security. 

**I believe Arnaud had a slightly different intent:**  an Open/Closed sensor that was 
physically separated from the Lock so the sensor can be used to both unlock and lock 
the specified Lock.

## How mine is different
The SmartApp is used to help ensure a door stay locked with no user intervention. 

In my SmartApp, there is never a case where I want the SmartApp to execute `unlock`
because my `Open/Closed Sensor` is physically located on the same door as the `Lock`.

## High level Logic

* This SmartApp monitors the specified `Open/Closed Sensor` (door open sensor) and `Lock` for events. 
* If an event shows the door is `closed` or the lock is `unlocked`, after N seconds the SmartApp will lock the `Lock`.
  * If, during that N seconds, you `open the door` or `lock` it, the auto-lock will not be performed.

## FAQ

**Q: Can't this be done without an "Open/Closed Sensor"?**

A: I don't think so. There are events when the lock is locked and unlocked, 
but the `Lock` doesn't know when the door is opened or closed. You could
modify the script to just lock the door N seconds after it was unlocked,
but that wouldn't provide the functionality I was looking for.
