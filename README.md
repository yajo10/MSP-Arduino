Arduino library for MSPv2 (MultiWii Serial Protocol)
===============================

It's a fork of https://github.com/fdivitto/MSP 

It simply uses bigger integers for message ID and payload size and includes the new tag and new checksum algorithm.

## Known Issues:
* no new message IDs are included yet (you may get them from https://github.com/iNavFlight/inav/tree/master/src/main/msp)

This is a simple library to send requests, commands or just wait messages from a MultiWii compatible flight controller (cleanflight, betaflight, etc...), specifically designed to work better with INAV.

MSP library can be attached to any serial port (hardware or software).

Not all MSP messages and commands are implemented. However new messages can be simply added.


Example to get RC channels:

```
MSP msp;

void setup()
{
  Serial.begin(115200);
  msp.begin(Serial);
}

void loop()
{
  msp_rc_t rc;
  if (msp.request(MSP_RC, &rc, sizeof(rc))) {
  	
    uint16_t roll     = rc.channelValue[0];
    uint16_t pitch    = rc.channelValue[1];
    uint16_t yaw      = rc.channelValue[2];
    uint16_t throttle = rc.channelValue[3];
    
  }
}
```

