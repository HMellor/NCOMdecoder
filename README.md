# NCOMdecoder [![Build Status](https://travis-ci.com/HMellor/NCOMdecoder.svg?branch=master)](https://travis-ci.com/HMellor/NCOMdecoder)
An NCOM decoder based in C for use with OxTS navigation systems, enabling users to decode the binary NCOM output. 

## Repository folders

### nav
This folder contains two library files `NcomRxC.h` and `NcomRxC.c`, which can be included in your project.

### example
The folder contains a simple program that exports an NCOM file to a CSV file, using the library files in `nav`. The program opens a file stream (to read the file), and decodes the NCOM packets from this stream.

## Instructions to build and run example program

***
NB: This has been tested on the following platforms:
* Unix (MacOS, Xenial)
* MINGW64 (Windows 10)

_Please note there appears to be an issue running in Cygwin._
***

```
# First clone this repository
git clone https://github.com/OxfordTechnicalSolutions/NCOMdecoder.git
cd NCOMdecoder

# Change directory into example source code folder
cd example

# Run make, which includes library files in nav (specified in Makefile)
make            

# Run executable, with example ncom data to create csv file
# Usage: NcomToCsv <input file> <output file> [<trig_file>]

./NcomToCsv 171019_031603.ncom 171019_031603.csv 

```

## Measurements

The following table lists all the measurements available in a standard NCOM packet. 

These can also be found in `measurements.csv`

| Store name           | Type     | Units  | Format            | Full name                                                    | Coordinate Frame             | Alternate Coordinate Frame Name                      | Description                                                                    | 
|----------------------|----------|--------|-------------------|--------------------------------------------------------------|------------------------------|------------------------------------------------------|--------------------------------------------------------------------------------| 
| Ax                   | double   | m/s²   | 0                 | Acceleration Xv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame longitudinal (forward) IMU acceleration                      | 
| Ay                   | double   | m/s²   | 0                 | Acceleration Yv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame lateral (right) IMU acceleration                             | 
| Az                   | double   | m/s²   | 0                 | Acceleration Zv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame vertical (down) IMU acceleration                             | 
| Af                   | double   | m/s²   | 0                 | Acceleration forward                                         | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame longitudinal (forward) IMU acceleration                  | 
| Al                   | double   | m/s²   | 0                 | Acceleration lateral                                         | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame lateral (right) IMU acceleration                         | 
| Ad                   | double   | m/s²   | 0                 | Acceleration down                                            | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame vertical (down) IMU acceleration                         | 
| FiltAx               | double   | m/s²   | 0                 | Acceleration filtered Xv                                     | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame longitudinal (forward) filtered IMU acceleration             | 
| FiltAy               | double   | m/s²   | 0                 | Acceleration filtered Yv                                     | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame lateral (right) filtered IMU acceleration                    | 
| FiltAz               | double   | m/s²   | 0                 | Acceleration filtered Zv                                     | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame vertical (down) filtered IMU acceleration                    | 
| FiltAf               | double   | m/s²   | 0                 | Acceleration filtered forward                                | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame longitudinal (forward) filtered IMU acceleration         | 
| FiltAl               | double   | m/s²   | 0                 | Acceleration filtered lateral                                | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame lateral (right) filtered IMU acceleration                | 
| FiltAd               | double   | m/s²   | 0                 | Acceleration filtered down                                   | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame vertical (down) filtered IMU acceleration                | 
| IsoAnX               | double   | m/s²   | 0                 | ISO e.f.s. east acceleration                                 | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system east acceleration                                  | 
| IsoAnY               | double   | m/s²   | 0                 | ISO e.f.s. north acceleration                                | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system north acceleration                                 | 
| IsoAnZ               | double   | m/s²   | 0                 | ISO e.f.s. vertical acceleration                             | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system vertical (up) acceleration                         | 
| IsoAhX               | double   | m/s²   | 0                 | ISO i.s. longitudinal acceleration                           | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system longitudinal (forward) acceleration               | 
| IsoAhY               | double   | m/s²   | 0                 | ISO i.s. lateral acceleration                                | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system lateral (left) acceleration                       | 
| IsoAhZ               | double   | m/s²   | 0                 | ISO i.s. vertical acceleration                               | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system vertical (up) acceleration                        | 
| IsoAoX               | double   | m/s²   | 0                 | ISO v.s. longitudinal acceleration                           | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system longitudinal (forward) acceleration                    | 
| IsoAoY               | double   | m/s²   | 0                 | ISO v.s. lateral acceleration                                | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system lateral (left) acceleration                            | 
| IsoAoZ               | double   | m/s²   | 0                 | ISO v.s. vertical acceleration                               | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system vertical (up) acceleration                             | 
| FiltIsoAnX           | double   | m/s²   | 0                 | ISO e.f.s. east filtered acceleration                        | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system east filtered acceleration                         | 
| FiltIsoAnY           | double   | m/s²   | 0                 | ISO e.f.s. north filtered acceleration                       | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system north filtered acceleration                        | 
| FiltIsoAnZ           | double   | m/s²   | 0                 | ISO e.f.s. vertical filtered acceleration                    | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system vertical (up) filtered acceleration                | 
| FiltIsoAhX           | double   | m/s²   | 0                 | ISO i.s. longitudinal filtered acceleration                  | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system longitudinal (forward) filtered acceleration      | 
| FiltIsoAhY           | double   | m/s²   | 0                 | ISO i.s. lateral filtered acceleration                       | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system lateral (left) filtered acceleration              | 
| FiltIsoAhZ           | double   | m/s²   | 0                 | ISO i.s. vertical filtered acceleration                      | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system vertical (up) filtered acceleration               | 
| FiltIsoAoX           | double   | m/s²   | 0                 | ISO v.s. longitudinal filtered acceleration                  | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system longitudinal (forward) filtered acceleration           | 
| FiltIsoAoY           | double   | m/s²   | 0                 | ISO v.s. lateral filtered acceleration                       | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system lateral (left) filtered acceleration                   | 
| FiltIsoAoZ           | double   | m/s²   | 0                 | ISO v.s. vertical filtered acceleration                      | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system vertical (up) filtered acceleration                    | 
| Yx                   | double   | deg/s² | 0                 | Angular acceleration Xv                                      | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame longitudinal (forward) IMU angular acceleration              | 
| Yy                   | double   | deg/s² | 0                 | Angular acceleration Yv                                      | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame lateral (right) IMU angular acceleration                     | 
| Yz                   | double   | deg/s² | 0                 | Angular acceleration Zv                                      | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame vertical (down) IMU angular acceleration                     | 
| Yf                   | double   | deg/s² | 0                 | Angular acceleration forward                                 | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame longitudinal (forward) IMU angular acceleration          | 
| Yl                   | double   | deg/s² | 0                 | Angular acceleration lateral                                 | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame lateral (right) IMU angular acceleration                 | 
| Yd                   | double   | deg/s² | 0                 | Angular acceleration down                                    | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame vertical (down) IMU angular acceleration                 | 
| FiltYx               | double   | deg/s² | 0                 | Angular acceleration filtered Xv                             | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame longitudinal (forward) filtered IMU angular acceleration     | 
| FiltYy               | double   | deg/s² | 0                 | Angular acceleration filtered Yv                             | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame lateral (right) filtered IMU angular acceleration            | 
| FiltYz               | double   | deg/s² | 0                 | Angular acceleration filtered Zv                             | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame vertical (down) filtered IMU angular acceleration            | 
| FiltYf               | double   | deg/s² | 0                 | Angular acceleration filtered forward                        | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame longitudinal (forward) filtered IMU angular acceleration | 
| FiltYl               | double   | deg/s² | 0                 | Angular acceleration filtered lateral                        | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame lateral (right) filtered IMU angular acceleration        | 
| FiltYd               | double   | deg/s² | 0                 | Angular acceleration filtered down                           | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame vertical (down) filtered IMU angular acceleration        | 
| IsoYnX               | double   | deg/s² | 0                 | ISO e.f.s. roll acceleration                                 | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system roll (east angular) acceleration                   | 
| IsoYnY               | double   | deg/s² | 0                 | ISO e.f.s. pitch acceleration                                | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system pitch (north angular) acceleration                 | 
| IsoYnZ               | double   | deg/s² | 0                 | ISO e.f.s. yaw acceleration                                  | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system yaw (vertical angular) acceleration                | 
| IsoYhX               | double   | deg/s² | 0                 | ISO i.s. roll acceleration                                   | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system roll (longitudinal angular) acceleration          | 
| IsoYhY               | double   | deg/s² | 0                 | ISO i.s. pitch acceleration                                  | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system pitch (lateral angular) acceleration              | 
| IsoYhZ               | double   | deg/s² | 0                 | ISO i.s. yaw acceleration                                    | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system yaw (vertical angular) acceleration               | 
| IsoYoX               | double   | deg/s² | 0                 | ISO v.s. roll acceleration                                   | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system roll (longitudinal angular) acceleration               | 
| IsoYoY               | double   | deg/s² | 0                 | ISO v.s. pitch acceleration                                  | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system pitch (lateral angular) acceleration                   | 
| IsoYoZ               | double   | deg/s² | 0                 | ISO v.s. yaw acceleration                                    | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system yaw (vertical angular) acceleration                    | 
| FiltIsoYnX           | double   | deg/s² | 0                 | ISO e.f.s. roll filtered acceleration                        | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system roll (east angular) filtered acceleration          | 
| FiltIsoYnY           | double   | deg/s² | 0                 | ISO e.f.s. pitch filtered acceleration                       | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system pitch (north angular) filtered acceleration        | 
| FiltIsoYnZ           | double   | deg/s² | 0                 | ISO e.f.s. yaw filtered acceleration                         | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system yaw (vertical angular) filtered acceleration       | 
| FiltIsoYhX           | double   | deg/s² | 0                 | ISO i.s. roll filtered acceleration                          | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system roll (longitudinal angular) filtered acceleration | 
| FiltIsoYhY           | double   | deg/s² | 0                 | ISO i.s. pitch filtered acceleration                         | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system pitch (lateral angular) filtered acceleration     | 
| FiltIsoYhZ           | double   | deg/s² | 0                 | ISO i.s. yaw filtered acceleration                           | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system yaw (vertical angular) filtered acceleration      | 
| FiltIsoYoX           | double   | deg/s² | 0                 | ISO v.s. roll filtered acceleration                          | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system roll (longitudinal angular) filtered acceleration      | 
| FiltIsoYoY           | double   | deg/s² | 0                 | ISO v.s. pitch filtered acceleration                         | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system pitch (lateral angular) filtered acceleration          | 
| FiltIsoYoZ           | double   | deg/s² | 0                 | ISO v.s. yaw filtered acceleration                           | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system yaw (vertical angular) filtered acceleration           | 
| Wx                   | double   | deg/s  | 0                 | Angular rate Xv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame longitudinal (forward) IMU angular rate                      | 
| Wy                   | double   | deg/s  | 0                 | Angular rate Yv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame lateral (right) IMU angular rate                             | 
| Wz                   | double   | deg/s  | 0                 | Angular rate Zv                                              | OxTS vehicle frame           | OxTS output frame (with default output displacement) | OxTS output frame vertical (down) IMU angular rate                             | 
| Wf                   | double   | deg/s  | 0                 | Angular rate forward                                         | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame longitudinal (forward) IMU angular rate                  | 
| Wl                   | double   | deg/s  | 0                 | Angular rate lateral                                         | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame lateral (right) IMU angular rate                         | 
| Wd                   | double   | deg/s  | 0                 | Angular rate down                                            | OxTS horizontal frame        | OxTS level frame                                     | OxTS horizontal frame vertical (down) IMU angular rate                         | 
| IsoWnX               | double   | deg/s  | 0                 | ISO e.f.s. roll velocity                                     | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system roll (east angular) velocity                       | 
| IsoWnY               | double   | deg/s  | 0                 | ISO e.f.s. pitch velocity                                    | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system pitch (north angular) velocity                     | 
| IsoWnZ               | double   | deg/s  | 0                 | ISO e.f.s. yaw velocity                                      | ISO 8855 earth-fixed system  |                                                      | ISO 8855 earth-fixed system yaw (vertical angular) velocity                    | 
| IsoWhX               | double   | deg/s  | 0                 | ISO i.s. roll velocity                                       | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system roll (longitudinal angular) velocity              | 
| IsoWhY               | double   | deg/s  | 0                 | ISO i.s. pitch velocity                                      | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system pitch (lateral angular) velocity                  | 
| IsoWhZ               | double   | deg/s  | 0                 | ISO i.s. yaw velocity                                        | ISO 8855 intermediate system |                                                      | ISO 8855 intermediate system yaw (vertical angular) velocity                   | 
| IsoWoX               | double   | deg/s  | 0                 | ISO v.s. roll velocity                                       | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system roll (longitudinal angular) velocity                   | 
| IsoWoY               | double   | deg/s  | 0                 | ISO v.s. pitch velocity                                      | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system pitch (lateral angular) velocity                       | 
| IsoWoZ               | double   | deg/s  | 0                 | ISO v.s. yaw velocity                                        | ISO 8855 vehicle system      |                                                      | ISO 8855 vehicle system yaw (vertical angular) velocity                        | 
| HeadingAcc           | double   | deg    | 0                 | Heading accuracy                                             |                              |                                                      | Heading Accuracy                                                               | 
| PitchAcc             | double   | deg    | 0                 | Pitch accuracy                                               |                              |                                                      | Pitch Accuracy                                                                 | 
| RollAcc              | double   | deg    | 0                 | Roll accuracy                                                |                              |                                                      | Roll Accuracy                                                                  | 
| Track                | double   | deg    | 0                 | Track angle                                                  |                              |                                                      |                                                                                | 
| TrackAcc             | double   | deg    | 0                 | Track angle accuracy                                         |                              |                                                      |                                                                                | 
| Slip                 | double   | deg    | 0                 | Slip angle                                                   |                              |                                                      |                                                                                | 
| SlipAcc              | double   | deg    | 0                 | Slip angle accuracy                                          |                              |                                                      |                                                                                | 
| IsoYaw               | double   | deg    | 0                 | ISO yaw angle                                                |                              |                                                      | ISO 8855 yaw angle                                                             | 
| IsoPitch             | double   | deg    | 0                 | ISO pitch angle                                              |                              |                                                      | ISO 8855 pitch angle                                                           | 
| IsoRoll              | double   | deg    | 0                 | ISO roll angle                                               |                              |                                                      | ISO 8855 roll angle                                                            | 
| Surf2OutHeading      | double   | deg    | 0                 | Heading to surface                                           |                              |                                                      |                                                                                | 
| Surf2OutPitch        | double   | deg    | 0                 | Pitch to surface                                             |                              |                                                      |                                                                                | 
| Surf2OutRoll         | double   | deg    | 0                 | Roll to surface                                              |                              |                                                      |                                                                                | 
| Lat                  | double   | deg    | 0                 | Latitude                                                     |                              |                                                      | Latitude                                                                       | 
| Lon                  | double   | deg    | 0                 | Longitude                                                    |                              |                                                      | Longitude                                                                      | 
| Alt                  | double   | m      | 0                 | Altitude                                                     |                              |                                                      | Altitude                                                                       | 
| NorthAcc             | double   | m      | 0                 | Position accuracy north                                      |                              |                                                      | North Position Accuracy                                                        | 
| EastAcc              | double   | m      | 0                 | Position accuracy east                                       |                              |                                                      | East Position Accuracy                                                         | 
| AltAcc               | double   | m      | 0                 | Position accuracy down                                       |                              |                                                      | Down Position Accuracy                                                         | 
| Dist2d               | double   | m      | 0                 | Distance horizontal                                          |                              |                                                      | Distance travelled in horizontal directions                                    | 
| Dist3d               | double   | m      | 0                 | Distance 3D                                                  |                              |                                                      | Distance travelled in all directions                                           | 
| GpsPosMode           | int      |        | ~GpsXModeName (#) | GPS position mode                                            |                              |                                                      | Position mode of the GPS receiver being used for position                      | 
| GpsVelMode           | int      |        | ~GpsXModeName (#) | GPS velocity mode                                            |                              |                                                      | Velocity mode of the GPS receiver being used for velocity                      | 
| GpsAttMode           | int      |        | ~GpsXModeName (#) | GPS dual antenna attitude mode                               |                              |                                                      | Attitude (dual-antenna) mode of the GPS receivers                              | 
| GpsNumObs            | int      |        | #                 | Number of GPS satellites used                                |                              |                                                      | Number of GPS satellites tracked by the Primary GPS receiver                   | 
| GpsDiffAge           | double   | s      | 0                 | Differential GPS age                                         |                              |                                                      | Age of the current differential corrections                                    | 
| "Time            "   | double   |        |                   | Time in seconds from start of GPS time                       |                              |                                                      | Seconds from GPS time zero (0h 1980-01-06). [s]                                | 
| "TimeWeekCount    "  | uint32_t |        |                   | GPS time format week counter                                 |                              |                                                      | GPS time format week counter. [week]                                           | 
| "TimeWeekSecond    " | double   |        |                   | GPS time format seconds into week                            |                              |                                                      | GPS time format seconds into week. [s]                                         | 
| "TimeUtcOffset    "  | int      |        |                   | Offset between Coordinated Universal Time (UTC) and GPS time |                              |                                                      | Offset between Coordinated Universal Time (UTC) and GPS time. [s]              | 
| TrigTime             | double   |        |                   | Time of last trigger falling edge                            |                              |                                                      | Time of last trigger falling edge. [s]                                         | 
| Trig2Time            | double   |        |                   | Time of last trigger rising edge                             |                              |                                                      | Time of last trigger rising edge. [s]                                          | 

*This table is generated from .README.csv using https://donatstudios.com/CsvToMarkdownTable*
