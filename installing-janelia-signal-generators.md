# HHMI Janelia Signal Generator Installation

## 8 Channel Pulse Generator (based on Teensy board)

Start NI MAX without the pulse generator plugged in.  Open up `My System` then `Devices and Interfaces`.  Check out what's already there.

Plug in the 8 Channel Pulse Generator and press F5.  NI MAX will search for devices again; you should see a new one appear that looks something like

```
ASRL3::INSTR "COM3"
```

If you click on it, the right panel will tell you that the port description is "Teensy USB Serial".

You'll need to select this channel from within the MWT (i.e. `COM3` if that's where it is) to use the stimulator.

## Waveform generator (based on Arduino Pro Mini with )

Follow the same procedure as with the pulse generator, but look for "USB Serial Port".  The name is generic, but you can identify it by refreshing the list and watching for which new port appears.