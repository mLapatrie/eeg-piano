# Music Therapy with EEG Piano: Empowering Musical Expression for All

## Overview:<br/>
Music Therapy with EEG is a project that seeks to bring the therapeutic benefits of music to individuals with physical challenges, allowing them to actively participate in music therapy sessions. By using brainwave patterns captured through a homemade electroencephalogram (EEG) device, this tool allows users to control the pitch of musical notes, providing a unique and accessible way to play a musical instrument without requiring extensive physical dexterity.

## This repository contains:<br/>
The repository contains the schematic for the EEG device, 3D models for the piano key parts, code for EEG data processing and two different modes of piano playing that are explained in more details down below.

## How to use the device:<br/>
### 3D models
There are 3 models that can be printed to modify a limit switch into a piano key, making the experience more fun. The limit switch must then be placed between the GND and 7th pins on the Arduino UNO board. <br/>
<p align="center"><img src="https://github.com/mLapatrie/Music-Therapy-with-EEG-Piano/assets/48076370/228370ce-31d1-4e93-90fb-3885e621cd3c" width="400"></p>


### Electrode placement: 
Following the 10-20 system, the positive electrode should be placed on O2, the negative electrode on A2 and the ground electrode on A1. See image below. <br/>
<p align="center"><img src="https://github.com/mLapatrie/Music-Therapy-with-EEG-Piano/assets/48076370/a74677cd-b4fc-4e85-8730-517c0483152a" width="300"></p>

### Adjusting the EEG
The output of the EEG should go into the A0 pin of the Arduino UNO board. <br/>
After placing the electrodes, one should play with the gain to get the best possible resolution without clipping with the eeg_test.ino program. Then, looking at the time-frequency domain, the user needs to play with the amplitude variable to make sure that the alpha amplitude is between 0 and 255 since it is then parsed as an unsigned byte.

### Virtual piano
There are two modes that can be used with this program. The first one is a simple virtual piano that maps the amplitude of the alpha waves on two octaves of the piano. Then, when a button is pressed, the mapped note is played. This allows users to familiarize themselves with the machine. However, it is to note that controlling your alpha waves to this degree of precision is almost impossible. And althougth it can be fun for a while, the second mode makes the experience much better.

![image](https://github.com/mLapatrie/Music-Therapy-with-EEG-Piano/assets/48076370/4341188c-5dab-43c7-9f62-47022a725295)

### Accompanied virtual piano
The second mode plays a music track while the user plays the piano over it. It then tracks the inputs of the user and slightly corrects them if necessary to make the music sound more melodic. This tool is especially good with jazz music, but works with any type of music the user prefers. <br/>
Note: Right now, only jazz music is coded in the program, but it can be easily changed by changing the chords in the program and changing the background music file called chords.mp3.

## Troubleshooting
**The signal read by the arduino is 0.0**: If you've tried adjusting the gain of the EEG and the signal is stuck at zero, the signal may be negative. You can test this by interchanging the positive and the negative electrodes. If this doesn't work, try changing the resistor going from the inverting input to the output of the OP Amp to a higher value. This should drastically augment the gain and you should get a signal that clips a 1023.0. You can then play with the value of the gain to get a good signal. While doing all of this, make sure the impedance of your electrodes is at the lowest value possible.

**The signal read by the arduino is 1023.0***: If your signal is stuck at 1023.0, it means that your signal is too high for the Arduino to read. Try changing the gain by playing with the potentiometer.

If none of this works or your problem is not shown in the troubleshooting section, consider contacting me and I will be more than happy to help.
