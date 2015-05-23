# HHMI Janelia Signal Generator Installation

## 8 Channel Pulse Generator (based on Teensy board)

Start NI MAX without the pulse generator plugged in.  Open up `My System` then `Devices and Interfaces`.  Check out what's already there.

Plug in the 8 Channel Pulse Generator and press F5.  NI MAX will search for devices again; you should see a new one appear that looks something like

```
ASRL3::INSTR "COM3"
```

If you click on it, the right panel will tell you that the port description is "Teensy USB Serial".

The baud rate will probably be wrong (9600).  At the bottom of that panel are some easily overlooked tabs; "Settings" is selected by default.  Click on "Port settings" and change "Baud rate" to 115200.  Everything else should be okay.  (8 data bits, "None" for parity, 1 stop bit, "None" for flow control.)

There's another easy-to-overlook button at the top: `Save`.  Click it.  Now go back to the "Settings" tab; it should reflect the change you made.

