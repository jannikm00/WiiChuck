# WiiChuck
An Arduino library for  the Nunchuk Controller over I²C.

## Supported Controllers:

* Nunchuk


# Mapping

All controllers have been mapped across a single readable array so that code written for one Wii accessort can be made generic for all of Wii accessory devices. The values that come from the controller are scaled to a 0-255 range for all analog and for all digital values. Each value is stored in a single byte in the 'values[]' array, a public member of the accessory class. 

Initialize the controller first:

```
nunchuck1.begin();
```

In loop, when reading the controller values, first call:

```
nunchuck1.readData();    // Read inputs and update maps
```

Then read the controller values out of the 'values[]' array:

```
uint8_t joystickValueX = nunchuck1.values[1];
uint8_t joystickValueY = nunchuck1.values[2];

...

uint8_t lastValue = nunchuck1.values[19];

```

## Nunchuck mapping

```
	values[1]=map(getJoyX(),0,255,0,255);
	values[2]=map(getJoyY(),0,255,0,255);
	values[3]=map(getRollAngle(),0,1024,0,256);
	values[4]=map(getPitchAngle(),0,1024,0,256);
	values[5]=map(getAccelX(),0,1024,0,256);
	values[6]=map(getAccelY(),0,1024,0,256);

	values[7]=map(getAccelZ(),0,1024,0,256);
	values[8]=0;
	values[9]=0;
	values[10]=0;
	values[11]=getButtonZ()?255:0;
	values[12]=getButtonC()?255:0;
	values[13]=0;
	values[14]=0;

	values[15]=0;
	values[16]=0;
	values[17]=0;

	values[18]=0;
	values[19]=0;
```



# Repository Structure 
This repository is forked from a curated set of old Arduino Libraries. I kept the old commits and the fork linking to keep attribution to the work done before I picked up the torch. In my mind we all see farther by standing on the shoulders of giants, so it is only proper to give credit where credit is due.


