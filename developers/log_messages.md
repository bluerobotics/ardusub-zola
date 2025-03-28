+++
title = "Onboard Log Messages"
description = "Message listing for DataFlash autopilot logs."
date = 2023-05-04T17:13:47+10:00
template = "docs/page.html"
sort_by = "weight"
weight = 30
draft = false
[extra]
toc = true
top = false
external_redirect = "https://ardupilot.org/sub/docs/logmessages.html"
+++

<!-- Dynamically generated using Tools/autotest/logger_metadata/parse.py
DO NOT EDIT -->
This is a list of log messages which may be present in DataFlash (`.bin`) logs produced and stored onboard ArduSub vehicles (see [Log Parameters](../parameters/#log-parameters) for creation details). It is possible to [add a new message](https://ardupilot.org/dev/docs/code-overview-adding-a-new-log-message.html) by modifying the firmware.

DataFlash logs can be downloaded and analysed [from a computer](http://www.ardusub.com/reference/data-logging.html#downloading) or [through BlueOS](@/software/onboard/BlueOS-1.1/advanced-usage/index.md#log-browser).

## ACC
IMU accelerometer data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|accelerometer sensor instance number|
|SampleUS|time since system startup this sample was taken|
|AccX|acceleration along X axis|
|AccY|acceleration along Y axis|
|AccZ|acceleration along Z axis|

## ADSB
Automatic Dependant Serveillance - Broadcast detected vehicle information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|ICAO_address|Transponder address|
|Lat|Vehicle latitude|
|Lng|Vehicle longitude|
|Alt|Vehicle altitude|
|Heading|Vehicle heading|
|Hor_vel|Vehicle horizontal velocity|
|Ver_vel|Vehicle vertical velocity|
|Squark|Transponder squawk code|

## AHR2
Backup AHRS data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Roll|Estimated roll|
|Pitch|Estimated pitch|
|Yaw|Estimated yaw|
|Alt|Estimated altitude|
|Lat|Estimated latitude|
|Lng|Estimated longitude|
|Q1|Estimated attitude quaternion component 1|
|Q2|Estimated attitude quaternion component 2|
|Q3|Estimated attitude quaternion component 3|
|Q4|Estimated attitude quaternion component 4|

## AOA
Angle of attack and Side Slip Angle values

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|AOA|Angle of Attack calculated from airspeed, wind vector,velocity vector |
|SSA|Side Slip Angle calculated from airspeed, wind vector,velocity vector|

## ARM
Arming status changes

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|ArmState|true if vehicle is now armed|
|ArmChecks|arming bitmask at time of arming|
|Forced|true if arm/disarm was forced|
|Method|method used for arming|

## ARSP
Airspeed sensor data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|Airspeed sensor instance number|
|Airspeed|Current airspeed|
|DiffPress|Pressure difference between static and dynamic port|
|Temp|Temperature used for calculation|
|RawPress|Raw pressure less offset|
|Offset|Offset from parameter|
|U|True if sensor is being used|
|H|True if sensor is healthy|
|Hfp|Probability sensor has failed|
|Pri|True if sensor is the primary sensor|

## ASM1
AirSim simulation data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TUS|Simulation's timestamp|
|R|Simulation's roll|
|P|Simulation's pitch|
|Y|Simulation's yaw|
|GX|Simulated gyroscope, X-axis|
|GY|Simulated gyroscope, Y-axis|
|GZ|Simulated gyroscope, Z-axis|

## ASM2
More AirSim simulation data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|AX|simulation's acceleration, X-axis|
|AY|simulation's acceleration, Y-axis|
|AZ|simulation's acceleration, Z-axis|
|VX|simulation's velocity, X-axis|
|VY|simulation's velocity, Y-axis|
|VZ|simulation's velocity, Z-axis|
|PX|simulation's position, X-axis|
|PY|simulation's position, Y-axis|
|PZ|simulation's position, Z-axis|
|Alt|simulation's gps altitude|
|SD|simulation's earth-frame speed-down|

## ATDE
AutoTune data packet

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Angle|current angle|
|Rate|current angular rate|

## ATT
Canonical vehicle attitude

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|DesRoll|vehicle desired roll|
|Roll|achieved vehicle roll|
|DesPitch|vehicle desired pitch|
|Pitch|achieved vehicle pitch|
|DesYaw|vehicle desired yaw|
|Yaw|achieved vehicle yaw|
|ErrRP|lowest estimated gyro drift error|
|ErrYaw|difference between measured yaw and DCM yaw estimate|
|AEKF|active EKF type|

## AUXF
Auixillary function invocation information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|function|ID of triggered function|
|pos|switch position when function triggered|
|source|source of auxillary function invocation|
|result|true if function was successful|

## BARO
Gathered Barometer data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|barometer sensor instance number|
|Alt|calculated altitude|
|Press|measured atmospheric pressure|
|Temp|measured atmospheric temperature|
|CRt|derived climb rate from primary barometer|
|SMS|time last sample was taken|
|Offset|raw adjustment of barometer altitude, zeroed on calibration, possibly set by GCS|
|GndTemp|temperature on ground, specified by parameter or measured while on ground|
|Health|true if barometer is considered healthy|

## BAT
Gathered battery data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|battery instance number|
|Volt|measured voltage|
|VoltR|estimated resting voltage|
|Curr|measured current|
|CurrTot|consumed Ah, current * time|
|EnrgTot|consumed Wh, energy this battery has expended|
|Temp|measured temperature|
|Res|estimated battery resistance|
|RemPct|remaining percentage|

## BCL
Battery cell voltage information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|battery instance number|
|Volt|battery voltage|
|V1|first cell voltage|
|V2|second cell voltage|
|V3|third cell voltage|
|V4|fourth cell voltage|
|V5|fifth cell voltage|
|V6|sixth cell voltage|
|V7|seventh cell voltage|
|V8|eighth cell voltage|
|V9|ninth cell voltage|
|V10|tenth cell voltage|
|V11|eleventh cell voltage|
|V12|twelfth cell voltage|

## BCL2
Battery cell voltage information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|battery instance number|
|V13|thirteenth cell voltage|
|V14|fourteenth cell voltage|

## BCN
Beacon information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Health|True if beacon sensor is healthy|
|Cnt|Number of beacons being used|
|D0|Distance to first beacon|
|D1|Distance to second beacon|
|D2|Distance to third beacon|
|D3|Distance to fourth beacon|
|PosX|Calculated beacon position, x-axis|
|PosY|Calculated beacon position, y-axis|
|PosZ|Calculated beacon position, z-axis|

## CAM
Camera shutter information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|GPSTime|milliseconds since start of GPS week|
|GPSWeek|weeks since 5 Jan 1980|
|Lat|current latitude|
|Lng|current longitude|
|Alt|current altitude|
|RelAlt|current altitude relative to home|
|GPSAlt|altitude as reported by GPS|
|Roll|current vehicle roll|
|Pitch|current vehicle pitch|
|Yaw|current vehicle yaw|

## CMD
Executed mission command information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|CTot|Total number of mission commands|
|CNum|This command's offset in mission|
|CId|Command type|
|Prm1|Parameter 1|
|Prm2|Parameter 2|
|Prm3|Parameter 3|
|Prm4|Parameter 4|
|Lat|Command latitude|
|Lng|Command longitude|
|Alt|Command altitude|
|Frame|Frame used for position|

## COFS
Current compass learn offsets

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|OfsX|best learnt offset, x-axis|
|OfsY|best learnt offset, y-axis|
|OfsZ|best learnt offset, z-axis|
|Var|error of best offset vector|
|Yaw|best learnt yaw|
|WVar|error of best learn yaw|
|N|number of samples used|

## CSRV
Servo feedback data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Servo number this data relates to|
|Pos|Current servo position|
|Force|Force being applied|
|Speed|Current servo movement speed|
|Pow|Amount of rated power being applied|

## CTRL
Attitude Control oscillation monitor diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|RMSRollP|LPF Root-Mean-Squared Roll Rate controller P gain|
|RMSRollD|LPF Root-Mean-Squared Roll rate controller D gain|
|RMSPitchP|LPF Root-Mean-Squared Pitch Rate controller P gain|
|RMSPitchD|LPF Root-Mean-Squared Pitch Rate controller D gain|
|RMSYaw|LPF Root-Mean-Squared Yaw Rate controller P+D gain|

## CTUN
Control Tuning information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|ThI|throttle input|
|ABst|angle boost|
|ThO|throttle output|
|ThH|calculated hover throttle|
|DAlt|desired altitude|
|Alt|achieved altitude|
|BAlt|barometric altitude|
|DSAlt|desired rangefinder altitude|
|SAlt|achieved rangefinder altitude|
|TAlt|terrain altitude|
|DCRt|desired climb rate|
|CRt|climb rate|

## D16
Generic 16-bit-signed-integer storage

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Data type identifier|
|Value|Value|

## D32
Generic 32-bit-signed-integer storage

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Data type identifier|
|Value|Value|

## DFLT
Generic float storage

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Data type identifier|
|Value|Value|

## DMS
DataFlash-Over-MAVLink statistics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|N|Current block number|
|Dp|Number of times we rejected a write to the backend|
|RT|Number of blocks sent from the retry queue|
|RS|Number of resends of unacknowledged data made|
|Fa|Average number of blocks on the free list|
|Fmn|Minimum number of blocks on the free list|
|Fmx|Maximum number of blocks on the free list|
|Pa|Average number of blocks on the pending list|
|Pmn|Minimum number of blocks on the pending list|
|Pmx|Maximum number of blocks on the pending list|
|Sa|Average number of blocks on the sent list|
|Smn|Minimum number of blocks on the sent list|
|Smx|Maximum number of blocks on the sent list|

## DSF
Onboard logging statistics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Dp|Number of times we rejected a write to the backend|
|Blk|Current block number|
|Bytes|Current write offset|
|FMn|Minimum free space in write buffer in last time period|
|FMx|Maximum free space in write buffer in last time period|
|FAv|Average free space in write buffer in last time period|

## DSTL
Deepstall Landing data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Stg|Deepstall landing stage|
|THdg|Target heading|
|Lat|Landing point latitude|
|Lng|Landing point longitude|
|Alt|Landing point altitude|
|XT|Crosstrack error|
|Travel|Expected travel distance vehicle will travel from this point|
|L1I|L1 controller crosstrack integrator value|
|Loiter|wind estimate loiter angle flown|
|Des|Deepstall steering PID desired value|
|P|Deepstall steering PID Proportional response component|
|I|Deepstall steering PID Integral response component|
|D|Deepstall steering PID Derivative response component|

## DU16
Generic 16-bit-unsigned-integer storage

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Data type identifier|
|Value|Value|

## DU32
Generic 32-bit-unsigned-integer storage

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Data type identifier|
|Value|Value|

## EAH1
External AHRS data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Roll|euler roll|
|Pitch|euler pitch|
|Yaw|euler yaw|
|VN|velocity north|
|VE|velocity east|
|VD|velocity down|
|Lat|latitude|
|Lon|longitude|
|Alt|altitude AMSL|
|UXY|uncertainty in XY position|
|UV|uncertainty in velocity|
|UR|uncertainty in roll|
|UP|uncertainty in pitch|
|UY|uncertainty in yaw|

## ECYL
EFI per-cylinder information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Inst|Cylinder this data belongs to|
|IgnT|Ignition timing|
|InjT|Injection time|
|CHT|Cylinder head temperature|
|EGT|Exhaust gas temperature|
|Lambda|Estimated lambda coefficient (dimensionless ratio)|
|IDX|Index of the publishing ECU|

## EFI
Electronic Fuel Injection system data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|LP|Reported engine load|
|Rpm|Reported engine RPM|
|SDT|Spark Dwell Time|
|ATM|Atmospheric pressure|
|IMP|Intake manifold pressure|
|IMT|Intake manifold temperature|
|ECT|Engine Coolant Temperature|
|OilP|Oil Pressure|
|OilT|Oil temperature|
|FP|Fuel Pressure|
|FCR|Fuel Consumption Rate|
|CFV|Consumed fueld volume|
|TPS|Throttle Position|
|IDX|Index of the publishing ECU|

## EFI2
Electronic Fuel Injection system data - redux

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Healthy|True if EFI is healthy|
|ES|Engine state|
|GE|General error|
|CSE|Crankshaft sensor status|
|TS|Temperature status|
|FPS|Fuel pressure status|
|OPS|Oil pressure status|
|DS|Detonation status|
|MS|Misfire status|
|DebS|Debris status|
|SPU|Spark plug usage|
|IDX|Index of the publishing ECU|

## ERR
Specifically coded error messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Subsys|Subsystem in which the error occurred|
|ECode|Subsystem-specific error code|

## ESC
Feedback received from ESCs

|FieldName|Description|
|---|---|
|TimeUS|microseconds since system startup|
|Instance|ESC instance number|
|RPM|reported motor rotation rate|
|Volt|Perceived input voltage for the ESC|
|Curr|Perceived current through the ESC|
|Temp|ESC temperature in centi-degrees C|
|CTot|current consumed total mAh|
|MotTemp|measured motor temperature in centi-degrees C|
|Err|error rate|

## EV
Specifically coded event messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|Event identifier|

## FMT
Message defining the format of messages in this file ([Read more...](https://ardupilot.org/dev/docs/code-overview-adding-a-new-log-message.html))

|FieldName|Description|
|---|---|
|Type|unique-to-this-log identifier for message being defined|
|Length|the number of bytes taken up by this message (including all headers)|
|Name|name of the message being defined|
|Format|character string defining the C-storage-type of the fields in this message|
|Columns|the labels of the message being defined|

## FMTU
Message defining units and multipliers used for fields of other messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|FmtType|numeric reference to associated FMT message|
|UnitIds|each character refers to a UNIT message.  The unit at an offset corresponds to the field at the same offset in FMT.Format|
|MultIds|each character refers to a MULT message.  The multiplier at an offset corresponds to the field at the same offset in FMT.Format|

## FOLL
Follow library diagnostic data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Lat|Target latitude|
|Lon|Target longitude|
|Alt|Target absolute altitude|
|VelN|Target earth-frame velocity, North|
|VelE|Target earth-frame velocity, East|
|VelD|Target earth-frame velocity, Down|
|LatE|Vehicle latitude|
|LonE|Vehicle longitude|
|AltE|Vehicle absolute altitude|

## FTN
Filter Tuning Messages

|FieldName|Description|
|---|---|
|TimeUS|microseconds since system startup|
|NDn|number of active dynamic harmonic notches|
|DnF1|dynamic harmonic notch centre frequency for motor 1|
|DnF2|dynamic harmonic notch centre frequency for motor 2|
|DnF3|dynamic harmonic notch centre frequency for motor 3|
|DnF4|dynamic harmonic notch centre frequency for motor 4|

## FTN1
FFT Filter Tuning

|FieldName|Description|
|---|---|
|TimeUS|microseconds since system startup|
|PkAvg|peak noise frequency as an energy-weighted average of roll and pitch peak frequencies|
|BwAvg|bandwidth of weighted peak freqency where edges are determined by FFT_ATT_REF|
|DnF|dynamic harmonic notch centre frequency|
|SnX|signal-to-noise ratio on the roll axis|
|SnY|signal-to-noise ratio on the pitch axis|
|SnZ|signal-to-noise ratio on the yaw axis|
|FtX|harmonic fit on roll of the highest noise peak to the second highest noise peak|
|FtY|harmonic fit on pitch of the highest noise peak to the second highest noise peak|
|FtZ|harmonic fit on yaw of the highest noise peak to the second highest noise peak|
|FH|FFT health|
|Tc|FFT cycle time|

## FTN2
FFT Noise Frequency Peak

|FieldName|Description|
|---|---|
|TimeUS|microseconds since system startup|
|Id|peak id where 0 is the centre peak, 1 is the lower shoulder and 2 is the upper shoulder|
|PkX|noise frequency of the peak on roll|
|PkY|noise frequency of the peak on pitch|
|PkZ|noise frequency of the peak on yaw|
|DnF|dynamic harmonic notch centre frequency|
|BwX|bandwidth of the peak freqency on roll where edges are determined by FFT_ATT_REF|
|BwY|bandwidth of the peak freqency on pitch where edges are determined by FFT_ATT_REF|
|BwZ|bandwidth of the peak freqency on yaw where edges are determined by FFT_ATT_REF|
|EnX|power spectral density bin energy of the peak on roll|
|EnY|power spectral density bin energy of the peak on roll|
|EnZ|power spectral density bin energy of the peak on roll|

## GPA
GPS accuracy information

|FieldName|Description|
|---|---|
|I|GPS instance number|
|TimeUS|Time since system startup|
|VDop|vertical degree of procession|
|HAcc|horizontal position accuracy|
|VAcc|vertical position accuracy|
|SAcc|speed accuracy|
|YAcc|yaw accuracy|
|VV|true if vertical velocity is available|
|SMS|time since system startup this sample was taken|
|Delta|system time delta between the last two reported positions|

## GPS
Information received from GNSS systems attached to the autopilot

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|GPS instance number|
|Status|GPS Fix type; 2D fix, 3D fix etc.|
|GMS|milliseconds since start of GPS Week|
|GWk|weeks since 5 Jan 1980|
|NSats|number of satellites visible|
|HDop|horizontal precision|
|Lat|latitude|
|Lng|longitude|
|Alt|altitude|
|Spd|ground speed|
|GCrs|ground course|
|VZ|vertical speed|
|Yaw|vehicle yaw|
|U|boolean value indicating whether this GPS is in use|

## GRAW
Raw uBlox data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|WkMS|receiver TimeOfWeek measurement|
|Week|GPS week|
|numSV|number of space vehicles seen|
|sv|space vehicle number of first vehicle|
|cpMes|carrier phase measurement|
|prMes|pseudorange measurement|
|doMes|Doppler measurement|
|mesQI|measurement quality index|
|cno|carrier-to-noise density ratio|
|lli|loss of lock indicator|

## GRXH
Raw uBlox data - header

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|rcvTime|receiver TimeOfWeek measurement|
|week|GPS week|
|leapS|GPS leap seconds|
|numMeas|number of space-vehicle measurements to follow|
|recStat|receiver tracking status bitfield|

## GRXS
Raw uBlox data - space-vehicle data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|prMes|Pseudorange measurement|
|cpMes|Carrier phase measurement|
|doMes|Doppler measurement|
|gnss|GNSS identifier|
|sv|Satellite identifier|
|freq|GLONASS frequency slot|
|lock|carrier phase locktime counter|
|cno|carrier-to-noise density ratio|
|prD|estimated pseudorange measurement standard deviation|
|cpD|estimated carrier phase measurement standard deviation|
|doD|estimated Doppler measurement standard deviation|
|trk|tracking status bitfield|

## GUID
Guided mode target information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Type|Type of guided mode|
|pX|Target position, X-Axis|
|pY|Target position, Y-Axis|
|pZ|Target position, Z-Axis|
|vX|Target velocity, X-Axis|
|vY|Target velocity, Y-Axis|
|vZ|Target velocity, Z-Axis|

## GYR
IMU gyroscope data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|gyroscope sensor instance number|
|SampleUS|time since system startup this sample was taken|
|GyrX|measured rotation rate about X axis|
|GyrY|measured rotation rate about Y axis|
|GyrZ|measured rotation rate about Z axis|

## HEAT
IMU Heater data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Temp|Current IMU temperature|
|Targ|Target IMU temperature|
|P|Proportional portion of response|
|I|Integral portion of response|
|Out|Controller output to heating element|

## ICMB
ICM20789 diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Traw|raw temperature from sensor|
|Praw|raw pressure from sensor|
|P|pressure|
|T|temperature|

## IMU
Inertial Measurement Unit data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|IMU sensor instance number|
|GyrX|measured rotation rate about X axis|
|GyrY|measured rotation rate about Y axis|
|GyrZ|measured rotation rate about Z axis|
|AccX|acceleration along X axis|
|AccY|acceleration along Y axis|
|AccZ|acceleration along Z axis|
|EG|gyroscope error count|
|EA|accelerometer error count|
|T|IMU temperature|
|GH|gyroscope health|
|AH|accelerometer health|
|GHz|gyroscope measurement rate|
|AHz|accelerometer measurement rate|

## IOMC
IOMCU diagnostic information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Mem|Free memory|
|TS|IOMCU uptime|
|NPkt|Number of packets received by IOMCU|
|Nerr|Protocol failures on MCU side|
|Nerr2|Reported number of failures on IOMCU side|
|NDel|Number of delayed packets received by MCU|

## JSN1
Log data received from JSON simulator

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup (us)|
|TStamp|Simulation's timestamp (s)|
|R|Simulation's roll (rad)|
|P|Simulation's pitch (rad)|
|Y|Simulation's yaw (rad)|
|GX|Simulated gyroscope, X-axis (rad/sec)|
|GY|Simulated gyroscope, Y-axis (rad/sec)|
|GZ|Simulated gyroscope, Z-axis (rad/sec)|

## JSN2
Log data received from JSON simulator

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup (us)|
|VN|simulation's velocity, North-axis (m/s)|
|VE|simulation's velocity, East-axis (m/s)|
|VD|simulation's velocity, Down-axis (m/s)|
|AX|simulation's acceleration, X-axis (m/s^2)|
|AY|simulation's acceleration, Y-axis (m/s^2)|
|AZ|simulation's acceleration, Z-axis (m/s^2)|
|AN|simulation's acceleration, North (m/s^2)|
|AE|simulation's acceleration, East (m/s^2)|
|AD|simulation's acceleration, Down (m/s^2)|

## LAND
Slope Landing data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|stage|progress through landing sequence|
|f1|Landing flags|
|f2|Slope-specific landing flags|
|slope|Slope to landing point|
|slopeInit|Initial slope to landing point|
|altO|Rangefinder correction|
|fh|Height for flare timing.|

## LGR
Landing gear information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|LandingGear|Current landing gear state|
|WeightOnWheels|True if there is weight on wheels|

## MAG
Information received from compasses

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|I|magnetometer sensor instance number|
|MagX|magnetic field strength in body frame|
|MagY|magnetic field strength in body frame|
|MagZ|magnetic field strength in body frame|
|OfsX|magnetic field offset in body frame|
|OfsY|magnetic field offset in body frame|
|OfsZ|magnetic field offset in body frame|
|MOX|motor interference magnetic field offset in body frame|
|MOY|motor interference magnetic field offset in body frame|
|MOZ|motor interference magnetic field offset in body frame|
|Health|true if the compass is considered healthy|
|S|time measurement was taken|

## MAV
GCS MAVLink link statistics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|chan|mavlink channel number|
|txp|transmitted packet count|
|rxp|received packet count|
|rxdp|perceived number of packets we never received|
|flags|compact representation of some stage of the channel|
|ss|stream slowdown is the number of ms being added to each message to fit within bandwidth|
|tf|times buffer was full when a message was going to be sent|

## MAVC
MAVLink command we have just executed

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TS|target system for command|
|TC|target component for command|
|Fr|command frame|
|Cmd|mavlink command enum value|
|Cur|current flag from mavlink packet|
|AC|autocontinue flag from mavlink packet|
|P1|first parameter from mavlink packet|
|P2|second parameter from mavlink packet|
|P3|third parameter from mavlink packet|
|P4|fourth parameter from mavlink packet|
|X|X coordinate from mavlink packet|
|Y|Y coordinate from mavlink packet|
|Z|Z coordinate from mavlink packet|
|Res|command result being returned from autopilot|
|WL|true if this command arrived via a COMMAND_LONG rather than COMMAND_INT|

## MMO
MMC3416 compass data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Nx|new measurement X axis|
|Ny|new measurement Y axis|
|Nz|new measurement Z axis|
|Ox|new offset X axis|
|Oy|new offset Y axis|
|Oz|new offset Z axis|

## MODE
vehicle control mode information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Mode|vehicle-specific mode number|
|ModeNum|alias for Mode|
|Rsn|reason for entering this mode; enumeration value|

## MON
Main loop stuck data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|LDelay|Time main loop has been stuck for|
|Task|Current scheduler task number|
|IErr|Internal error mask; which internal errors have been detected|
|IErrCnt|Internal error count; how many internal errors have been detected|
|IErrLn|Line on which internal error ocurred|
|MavMsg|Id of the last mavlink message processed|
|MavCmd|Id of the last mavlink command processed|
|SemLine|Line number of semaphore most recently taken|
|SPICnt|Number of SPI transactions processed|
|I2CCnt|Number of i2c transactions processed|

## MOTB
Battery information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|LiftMax|Maximum motor compensation gain|
|BatVolt|Ratio betwen detected battery voltage and maximum battery voltage|
|BatRes|Estimated battery resistance|
|ThLimit|Throttle limit set due to battery current limitations|

## MPPT
Information about the Maximum Power Point Tracker sensor

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Inst|Driver Instance|
|SN|Serial number|
|F|Faults|
|Temp|Temperature|
|InV|Input Voltage|
|InC|Input Current|
|InP|Input Power|
|OutV|Output Voltage|
|OutC|Output Current|
|OutP|Output Power|

## MSG
Textual messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Message|message text|

## MULT
Message mapping from single character to numeric multiplier

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|character referenced by FMTU|
|Mult|numeric multiplier|

## NKF0
EKF2 beacon sensor diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|ID|Beacon sensor ID|
|rng|Beacon range|
|innov|Beacon range innovation|
|SIV|sqrt of beacon range innovation variance|
|TR|Beacon range innovation consistency test ratio|
|BPN|Beacon north position|
|BPE|Beacon east position|
|BPD|Beacon down position|
|OFH|High estimate of vertical position offset of beacons rel to EKF origin|
|OFL|Low estimate of vertical position offset of beacons rel to EKF origin|
|OFN|always zero|
|OFE|always zero|
|OFD|always zero|

## NKF1
EKF2 estimator outputs

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|Roll|Estimated roll|
|Pitch|Estimated pitch|
|Yaw|Estimated yaw|
|VN|Estimated velocity (North component)|
|VE|Estimated velocity (East component)|
|VD|Estimated velocity (Down component)|
|dPD|Filtered derivative of vertical position (down)|
|PN|Estimated distance from origin (North component)|
|PE|Estimated distance from origin (East component)|
|PD|Estimated distance from origin (Down component)|
|GX|Estimated gyro bias, X axis|
|GY|Estimated gyro bias, Y axis|
|GZ|Estimated gyro bias, Z axis|
|OH|Height of origin above WGS-84|

## NKF2
EKF2 estimator secondary outputs

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|AZbias|Estimated accelerometer Z bias|
|GSX|Gyro Scale Factor (X-axis)|
|GSY|Gyro Scale Factor (Y-axis)|
|GSZ|Gyro Scale Factor (Z-axis)|
|VWN|Estimated wind velocity (North component)|
|VWE|Estimated wind velocity (East component)|
|MN|Magnetic field strength (North component)|
|ME|Magnetic field strength (East component)|
|MD|Magnetic field strength (Down component)|
|MX|Magnetic field strength (body X-axis)|
|MY|Magnetic field strength (body Y-axis)|
|MZ|Magnetic field strength (body Z-axis)|
|MI|Magnetometer used for data|

## NKF3
EKF2 innovations

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|IVN|Innovation in velocity (North component)|
|IVE|Innovation in velocity (East component)|
|IVD|Innovation in velocity (Down component)|
|IPN|Innovation in position (North component)|
|IPE|Innovation in position (East component)|
|IPD|Innovation in position (Down component)|
|IMX|Innovation in magnetic field strength (X-axis component)|
|IMY|Innovation in magnetic field strength (Y-axis component)|
|IMZ|Innovation in magnetic field strength (Z-axis component)|
|IYAW|Innovation in vehicle yaw|
|IVT|Innovation in true-airspeed|
|RErr|Accumulated relative error of this core with respect to active primary core|
|ErSc|A consolidated error score where higher numbers are less healthy|

## NKF4
EKF2 variances

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|SV|Square root of the velocity variance|
|SP|Square root of the position variance|
|SH|Square root of the height variance|
|SM|Magnetic field variance|
|SVT|tilt error convergence metric|
|errRP|Filtered error in roll/pitch estimate|
|OFN|Most recent position reset (North component)|
|OFE|Most recent position reset (East component)|
|FS|Filter fault status|
|TS|Filter timeout status bitmask (0:position measurement, 1:velocity measurement, 2:height measurement, 3:magnetometer measurement, 4:airspeed measurement)|
|SS|Filter solution status|
|GPS|Filter GPS status|
|PI|Primary core index|

## NKF5
EKF2 Sensor innovations (primary core) and general dumping ground

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|NI|Normalised flow variance|
|FIX|Optical flow LOS rate vector innovations from the main nav filter (X-axis)|
|FIY|Optical flow LOS rate vector innovations from the main nav filter (Y-axis)|
|AFI|Optical flow LOS rate innovation from terrain offset estimator|
|HAGL|Height above ground level|
|offset|Estimated vertical position of the terrain relative to the nav filter zero datum|
|RI|Range finder innovations|
|rng|Measured range|
|Herr|Filter ground offset state error|
|eAng|Magnitude of angular error|
|eVel|Magnitude of velocity error|
|ePos|Magnitude of position error|

## NKQ
EKF2 quaternion defining the rotation from NED to XYZ (autopilot) axes

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF2 core this data is for|
|Q1|Quaternion a term|
|Q2|Quaternion b term|
|Q3|Quaternion c term|
|Q4|Quaternion d term|

## NKT
EKF2 timing information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this message instance applies to|
|Cnt|count of samples used to create this message|
|IMUMin|smallest IMU sample interval|
|IMUMax|largest IMU sample interval|
|EKFMin|low-passed achieved average time step rate for the EKF (minimum)|
|EKFMax|low-passed achieved average time step rate for the EKF (maximum)|
|AngMin|accumulated measurement time interval for the delta angle (minimum)|
|AngMax|accumulated measurement time interval for the delta angle (maximum)|
|VMin|accumulated measurement time interval for the delta velocity (minimum)|
|VMax|accumulated measurement time interval for the delta velocity (maximum)|

## NKY0
EKF Yaw Estimator States

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this data is for|
|YC|GSF yaw estimate (rad)|
|YCS|GSF yaw estimate 1-Sigma uncertainty (rad)|
|Y0|Yaw estimate from individual EKF filter 0 (rad)|
|Y1|Yaw estimate from individual EKF filter 1 (rad)|
|Y2|Yaw estimate from individual EKF filter 2 (rad)|
|Y3|Yaw estimate from individual EKF filter 3 (rad)|
|Y4|Yaw estimate from individual EKF filter 4 (rad)|
|W0|Weighting applied to yaw estimate from individual EKF filter 0|
|W1|Weighting applied to yaw estimate from individual EKF filter 1|
|W2|Weighting applied to yaw estimate from individual EKF filter 2|
|W3|Weighting applied to yaw estimate from individual EKF filter 3|
|W4|Weighting applied to yaw estimate from individual EKF filter 4|

## NKY1
EKF Yaw Estimator Innovations

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this data is for|
|IVN0|North velocity innovation from individual EKF filter 0 (m/s)|
|IVN1|North velocity innovation from individual EKF filter 1 (m/s)|
|IVN2|North velocity innovation from individual EKF filter 2 (m/s)|
|IVN3|North velocity innovation from individual EKF filter 3 (m/s)|
|IVN4|North velocity innovation from individual EKF filter 4 (m/s)|
|IVE0|East velocity innovation from individual EKF filter 0 (m/s)|
|IVE1|East velocity innovation from individual EKF filter 1 (m/s)|
|IVE2|East velocity innovation from individual EKF filter 2 (m/s)|
|IVE3|East velocity innovation from individual EKF filter 3 (m/s)|
|IVE4|East velocity innovation from individual EKF filter 4 (m/s)|

## OABR
Object avoidance (Bendy Ruler) diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Type|Type of BendyRuler currently active|
|Act|True if Bendy Ruler avoidance is being used|
|DYaw|Best yaw chosen to avoid obstacle|
|Yaw|Current vehicle yaw|
|DP|Desired pitch chosen to avoid obstacle|
|RChg|True if BendyRuler resisted changing bearing and continued in last calculated bearing|
|Mar|Margin from path to obstacle on best yaw chosen|
|DLt|Destination latitude|
|DLg|Destination longitude|
|DAlt|Desired alt above EKF Origin|
|OLt|Intermediate location chosen for avoidance|
|OLg|Intermediate location chosen for avoidance|
|OAlt|Intermediate alt chosen for avoidance above EKF origin|

## OADJ
Object avoidance (Dijkstra) diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|State|Dijkstra avoidance library state|
|Err|Dijkstra library error condition|
|CurrPoint|Destination point in calculated path to destination|
|TotPoints|Number of points in path to destination|
|DLat|Destination latitude|
|DLng|Destination longitude|
|OALat|Object Avoidance chosen destination point latitude|
|OALng|Object Avoidance chosen destination point longitude|

## OF
Optical flow sensor data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Qual|Estimated sensor data quality|
|flowX|Sensor flow rate, X-axis|
|flowY|Sensor flow rate,Y-axis|
|bodyX|derived velocity, X-axis|
|bodyY|derived velocity, Y-axis|

## ORGN
Vehicle navigation origin or other notable position

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Type|Position type|
|Lat|Position latitude|
|Lng|Position longitude|
|Alt|Position altitude|

## PARM
parameter value

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Name|parameter name|
|Value|parameter value|

## PIDA
Proportional/Integral/Derivative gain values for Roll/Pitch/Yaw/Altitude/Steering

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tar|desired value|
|Act|achieved value|
|Err|error between target and achieved|
|P|proportional part of PID|
|I|integral part of PID|
|D|derivative part of PID|
|FF|controller feed-forward portion of response|
|Dmod|scaler applied to D gain to reduce limit cycling|
|SRate|slew rate used in slew limiter|
|Limit|1 if I term is limited due to output saturation|

## PIDP
Proportional/Integral/Derivative gain values for Roll/Pitch/Yaw/Altitude/Steering

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tar|desired value|
|Act|achieved value|
|Err|error between target and achieved|
|P|proportional part of PID|
|I|integral part of PID|
|D|derivative part of PID|
|FF|controller feed-forward portion of response|
|Dmod|scaler applied to D gain to reduce limit cycling|
|SRate|slew rate used in slew limiter|
|Limit|1 if I term is limited due to output saturation|

## PIDR
Proportional/Integral/Derivative gain values for Roll/Pitch/Yaw/Altitude/Steering

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tar|desired value|
|Act|achieved value|
|Err|error between target and achieved|
|P|proportional part of PID|
|I|integral part of PID|
|D|derivative part of PID|
|FF|controller feed-forward portion of response|
|Dmod|scaler applied to D gain to reduce limit cycling|
|SRate|slew rate used in slew limiter|
|Limit|1 if I term is limited due to output saturation|

## PIDS
Proportional/Integral/Derivative gain values for Roll/Pitch/Yaw/Altitude/Steering

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tar|desired value|
|Act|achieved value|
|Err|error between target and achieved|
|P|proportional part of PID|
|I|integral part of PID|
|D|derivative part of PID|
|FF|controller feed-forward portion of response|
|Dmod|scaler applied to D gain to reduce limit cycling|
|SRate|slew rate used in slew limiter|
|Limit|1 if I term is limited due to output saturation|

## PIDY
Proportional/Integral/Derivative gain values for Roll/Pitch/Yaw/Altitude/Steering

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tar|desired value|
|Act|achieved value|
|Err|error between target and achieved|
|P|proportional part of PID|
|I|integral part of PID|
|D|derivative part of PID|
|FF|controller feed-forward portion of response|
|Dmod|scaler applied to D gain to reduce limit cycling|
|SRate|slew rate used in slew limiter|
|Limit|1 if I term is limited due to output saturation|

## PL
Precision Landing messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Heal|True if Precision Landing is healthy|
|TAcq|True if landing target is detected|
|pX|Target position relative to vehicle, X-Axis (0 if target not found)|
|pY|Target position relative to vehicle, Y-Axis (0 if target not found)|
|vX|Target velocity relative to vehicle, X-Axis (0 if target not found)|
|vY|Target velocity relative to vehicle, Y-Axis (0 if target not found)|
|mX|Target's relative to origin position as 3-D Vector, X-Axis|
|mY|Target's relative to origin position as 3-D Vector, Y-Axis|
|mZ|Target's relative to origin position as 3-D Vector, Z-Axis|
|LastMeasMS|Time when target was last detected|
|EKFOutl|EKF's outlier count|
|Est|Type of estimator used|

## PM
autopilot system performance and general data dumping ground

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|NLon|Number of long loops detected|
|NLoop|Number of measurement loops for this message|
|MaxT|Maximum loop time|
|Mem|Free memory available|
|Load|System processor load|
|IntE|Internal error mask; which internal errors have been detected|
|ErrL|Internal error line number; last line number on which a internal error was detected|
|ErrC|Internal error count; how many internal errors have been detected|
|SPIC|Number of SPI transactions processed|
|I2CC|Number of i2c transactions processed|
|I2CI|Number of i2c interrupts serviced|
|Ex|number of microseconds being added to each loop to address scheduler overruns|

## POS
Canonical vehicle position

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Lat|Canonical vehicle latitude|
|Lng|Canonical vehicle longitude|
|Alt|Canonical vehicle altitude|
|RelHomeAlt|Canonical vehicle altitude relative to home|
|RelOriginAlt|Canonical vehicle altitude relative to navigation origin|

## POWR
System power information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Vcc|Flight board voltage|
|VServo|Servo rail voltage|
|Flags|System power flags|
|AccFlags|Accumulated System power flags; all flags which have ever been set|
|Safety|Hardware Safety Switch status|

## PRTN
Plane Parameter Tuning data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Set|Parameter set being tuned|
|Parm|Parameter being tuned|
|Value|Current parameter value|
|CenterValue|Center value (startpoint of current modifications) of parameter being tuned|

## PRX
Proximity Filtered sensor data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Layer|Pitch(instance) at which the obstacle is at. 0th layer {-75,-45} degrees. 1st layer {-45,-15} degrees. 2nd layer {-15, 15} degrees. 3rd layer {15, 45} degrees. 4th layer {45,75} degrees. Minimum distance in each layer will be logged.|
|He|True if proximity sensor is healthy|
|D0|Nearest object in sector surrounding 0-degrees|
|D45|Nearest object in sector surrounding 45-degrees|
|D90|Nearest object in sector surrounding 90-degrees|
|D135|Nearest object in sector surrounding 135-degrees|
|D180|Nearest object in sector surrounding 180-degrees|
|D225|Nearest object in sector surrounding 225-degrees|
|D270|Nearest object in sector surrounding 270-degrees|
|D315|Nearest object in sector surrounding 315-degrees|
|DUp|Nearest object in upwards direction|
|CAn|Angle to closest object|
|CDis|Distance to closest object|

## PRXR
Proximity Raw sensor data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Layer|Pitch(instance) at which the obstacle is at. 0th layer {-75,-45} degrees. 1st layer {-45,-15} degrees. 2nd layer {-15, 15} degrees. 3rd layer {15, 45} degrees. 4th layer {45,75} degrees. Minimum distance in each layer will be logged.|
|D0|Nearest object in sector surrounding 0-degrees|
|D45|Nearest object in sector surrounding 45-degrees|
|D90|Nearest object in sector surrounding 90-degrees|
|D135|Nearest object in sector surrounding 135-degrees|
|D180|Nearest object in sector surrounding 180-degrees|
|D225|Nearest object in sector surrounding 225-degrees|
|D270|Nearest object in sector surrounding 270-degrees|
|D315|Nearest object in sector surrounding 315-degrees|

## PSCD
Position Control Down

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TPD|Target position relative to EKF origin|
|PD|Position relative to EKF origin|
|DVD|Desired velocity Down|
|TVD|Target velocity Down|
|VD|Velocity Down|
|DAD|Desired acceleration Down|
|TAD|Target acceleration Down|
|AD|Acceleration Down|

## PSCE
Position Control East

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TPE|Target position relative to EKF origin|
|PE|Position relative to EKF origin|
|DVE|Desired velocity East|
|TVE|Target velocity East|
|VE|Velocity East|
|DAE|Desired acceleration East|
|TAE|Target acceleration East|
|AE|Acceleration East|

## PSCN
Position Control North

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TPN|Target position relative to EKF origin|
|PN|Position relative to EKF origin|
|DVN|Desired velocity North|
|TVN|Target velocity North|
|VN|Velocity North|
|DAN|Desired acceleration North|
|TAN|Target acceleration North|
|AN|Acceleration North|

## RAD
Telemetry radio statistics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|RSSI|RSSI|
|RemRSSI|RSSI reported from remote radio|
|TxBuf|number of bytes in radio ready to be sent|
|Noise|local noise floor|
|RemNoise|local noise floor reported from remote radio|
|RxErrors|damaged packet count|
|Fixed|fixed damaged packet count|

## RALY
Rally point information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Tot|total number of rally points onboard|
|Seq|this rally point's sequence number|
|Lat|latitude of rally point|
|Lng|longitude of rally point|
|Alt|altitude of rally point|

## RATE
Desired and achieved vehicle attitude rates. Not logged in Fixed Wing Plane modes.

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|RDes|vehicle desired roll rate|
|R|achieved vehicle roll rate|
|ROut|normalized output for Roll|
|PDes|vehicle desired pitch rate|
|P|vehicle pitch rate|
|POut|normalized output for Pitch|
|Y|achieved vehicle yaw rate|
|YOut|normalized output for Yaw|
|YDes|vehicle desired yaw rate|
|ADes|desired vehicle vertical acceleration|
|A|achieved vehicle vertical acceleration|
|AOut|percentage of vertical thrust output current being used|

## RBCH
Replay Data Beacon Header

|FieldName|Description|
|---|---|

## RBCI
Replay Data Beacon Instance

|FieldName|Description|
|---|---|

## RBOH
Replay body odometry data

|FieldName|Description|
|---|---|

## RBRH
Replay Data Barometer Header

|FieldName|Description|
|---|---|

## RBRI
Replay Data Barometer Instance

|FieldName|Description|
|---|---|

## RCDA
Raw RC data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|TS|data arrival timestamp|
|Prot|Protocol currently being decoded|
|Len|Number of valid bytes in message|
|U0|first quartet of bytes|
|U1|second quartet of bytes|
|U2|third quartet of bytes|
|U3|fourth quartet of bytes|
|U4|fifth quartet of bytes|
|U5|sixth quartet of bytes|
|U6|seventh quartet of bytes|
|U7|eight quartet of bytes|
|U8|ninth quartet of bytes|
|U9|tenth quartet of bytes|

## RCIN
RC input channels to vehicle

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C1|channel 1 input|
|C2|channel 2 input|
|C3|channel 3 input|
|C4|channel 4 input|
|C5|channel 5 input|
|C6|channel 6 input|
|C7|channel 7 input|
|C8|channel 8 input|
|C9|channel 9 input|
|C10|channel 10 input|
|C11|channel 11 input|
|C12|channel 12 input|
|C13|channel 13 input|
|C14|channel 14 input|

## RCOU
Servo channel output values

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C1|channel 1 output|
|C2|channel 2 output|
|C3|channel 3 output|
|C4|channel 4 output|
|C5|channel 5 output|
|C6|channel 6 output|
|C7|channel 7 output|
|C8|channel 8 output|
|C9|channel 9 output|
|C10|channel 10 output|
|C11|channel 11 output|
|C12|channel 12 output|
|C13|channel 13 output|
|C14|channel 14 output|

## REPH
Replay external position data

|FieldName|Description|
|---|---|

## REV2
Replay Event

|FieldName|Description|
|---|---|

## REVH
Replay external position data

|FieldName|Description|
|---|---|

## REY3
Replay Euler Yaw event

|FieldName|Description|
|---|---|

## RFND
Rangefinder sensor information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|rangefinder instance number this data is from|
|Dist|Reported distance from sensor|
|Stat|Sensor state|
|Orient|Sensor orientation|

## RGPH
Replay Data GPS Header

|FieldName|Description|
|---|---|

## RGPI
Replay Data GPS Instance, infrequently changing data

|FieldName|Description|
|---|---|

## RGPJ
Replay Data GPS Instance - rapidly changing data

|FieldName|Description|
|---|---|

## RMGH
Replay Data Magnetometer Header

|FieldName|Description|
|---|---|

## RMGI
Replay Data Magnetometer Instance

|FieldName|Description|
|---|---|

## ROFH
Replay optical flow data

|FieldName|Description|
|---|---|

## RPM
Data from RPM sensors

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|rpm1|First sensor's data|
|rpm2|Second sensor's data|

## RRNH
Replay Data Rangefinder Header

|FieldName|Description|
|---|---|

## RRNI
Replay Data Rangefinder Instance

|FieldName|Description|
|---|---|

## RSO2
Replay Set Origin event

|FieldName|Description|
|---|---|

## RSSI
Received Signal Strength Indicator for RC receiver

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|RXRSSI|RSSI|

## RVOH
Replay Data Visual Odometry data

|FieldName|Description|
|---|---|

## RWA2
Replay set-default-airspeed event

|FieldName|Description|
|---|---|

## RWOH
Replay wheel odometry data

|FieldName|Description|
|---|---|

## SA
Simple Avoidance messages

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|State|True if Simple Avoidance is active|
|DVelX|Desired velocity, X-Axis (Velocity before Avoidance)|
|DVelY|Desired velocity, Y-Axis (Velocity before Avoidance)|
|DVelZ|Desired velocity, Z-Axis (Velocity before Avoidance)|
|MVelX|Modified velocity, X-Axis (Velocity after Avoidance)|
|MVelY|Modified velocity, Y-Axis (Velocity after Avoidance)|
|MVelZ|Modified velocity, Z-Axis (Velocity after Avoidance)|
|Back|True if vehicle is backing away|

## SBPH
Swift Health Data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|CrcError|Number of packet CRC errors on serial connection|
|LastInject|Timestamp of last raw data injection to GPS|
|IARhyp|Current number of integer ambiguity hypotheses|

## SBRH
Swift Raw Message Data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|msg_flag|Swift message type|
|1|Sender ID|
|2|index; always 1|
|3|pages; number of pages received|
|4|msg length; number of bytes received|
|5|unused; always zero|
|6|data received from device|

## SIM
SITL simulator state

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Roll|Simulated roll|
|Pitch|Simulated pitch|
|Yaw|Simulated yaw|
|Alt|Simulated altitude|
|Lat|Simulated latitude|
|Lng|Simulated longitude|
|Q1|Attitude quaternion component 1|
|Q2|Attitude quaternion component 2|
|Q3|Attitude quaternion component 3|
|Q4|Attitude quaternion component 4|

## SIM2
Additional simulator state

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|PN|North position from home|
|PE|East position from home|
|PD|Down position from home|
|VN|Velocity north|
|VE|Velocity east|
|VD|Velocity down|

## SITL
Simulation data

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|VN|Velocity - North component|
|VE|Velocity - East component|
|VD|Velocity - Down component|
|AN|Acceleration - North component|
|AE|Acceleration - East component|
|AD|Acceleration - Down component|
|PN|Position - North component|
|PE|Position - East component|
|PD|Position - Down component|

## SMOO
Smoothed sensor data fed to EKF to avoid inconsistencies

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|AEx|Angular Velocity (around x-axis)|
|AEy|Angular Velocity (around y-axis)|
|AEz|Angular Velocity (around z-axis)|
|DPx|Velocity (along x-axis)|
|DPy|Velocity (along y-axis)|
|DPz|Velocity (along z-axis)|
|R|Roll|
|P|Pitch|
|Y|Yaw|
|R2|DCM Roll|
|P2|DCM Pitch|
|Y2|DCM Yaw|

## SRTL
SmartRTL statistics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Active|true if SmartRTL could be used right now|
|NumPts|number of points currently in use|
|MaxPts|maximum number of points that could be used|
|Action|most recent internal action taken by SRTL library|
|N|point associated with most recent action (North component)|
|E|point associated with most recent action (East component)|
|D|point associated with most recent action (Down component)|

## TERR
Terrain database infomration

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Status|Terrain database status|
|Lat|Current vehicle latitude|
|Lng|Current vehicle longitude|
|Spacing|terrain Tile spacing|
|TerrH|current Terrain height|
|CHeight|Vehicle height above terrain|
|Pending|Number of tile requests outstanding|
|Loaded|Number of tiles in memory|

## TRIG
Camera shutter information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|GPSTime|milliseconds since start of GPS week|
|GPSWeek|weeks since 5 Jan 1980|
|Lat|current latitude|
|Lng|current longitude|
|Alt|current altitude|
|RelAlt|current altitude relative to home|
|GPSAlt|altitude as reported by GPS|
|Roll|current vehicle roll|
|Pitch|current vehicle pitch|
|Yaw|current vehicle yaw|

## TSYN
Time synchronisation response information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|SysID|system ID this data is for|
|RTT|round trip time for this system|

## UBX1
uBlox-specific GPS information (part 1)

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|GPS instance number|
|noisePerMS|noise level as measured by GPS|
|jamInd|jamming indicator; higher is more likely jammed|
|aPower|antenna power indicator; 2 is don't know|
|agcCnt|automatic gain control monitor|
|config|bitmask for messages which haven't been seen|

## UBX2
uBlox-specific GPS information (part 2)

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Instance|GPS instance number|
|ofsI|imbalance of I part of complex signal|
|magI|magnitude of I part of complex signal|
|ofsQ|imbalance of Q part of complex signal|
|magQ|magnitude of Q part of complex signal|

## UNIT
Message mapping from single character to SI unit

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Id|character referenced by FMTU|
|Label|Unit - SI where available|

## VIBE
Processed (acceleration) vibration information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|IMU|Vibration instance number|
|VibeX|Primary accelerometer filtered vibration, x-axis|
|VibeY|Primary accelerometer filtered vibration, y-axis|
|VibeZ|Primary accelerometer filtered vibration, z-axis|
|Clip|Number of clipping events on 1st accelerometer|

## VISO
Visual Odometry

|FieldName|Description|
|---|---|
|TimeUS|System time|
|dt|Time period this data covers|
|AngDX|Angular change for body-frame roll axis|
|AngDY|Angular change for body-frame pitch axis|
|AngDZ|Angular change for body-frame z axis|
|PosDX|Position change for body-frame X axis (Forward-Back)|
|PosDY|Position change for body-frame Y axis (Right-Left)|
|PosDZ|Position change for body-frame Z axis (Down-Up)|
|conf|Confidence|

## VISP
Vision Position

|FieldName|Description|
|---|---|
|TimeUS|System time|
|RTimeUS|Remote system time|
|CTimeMS|Corrected system time|
|PX|Position X-axis (North-South)|
|PY|Position Y-axis (East-West)|
|PZ|Position Z-axis (Down-Up)|
|Roll|Roll lean angle|
|Pitch|Pitch lean angle|
|Yaw|Yaw angle|
|PErr|Position estimate error|
|AErr|Attitude estimate error|
|Rst|Position reset counter|
|Ign|Ignored|

## VISV
Vision Velocity

|FieldName|Description|
|---|---|
|TimeUS|System time|
|RTimeUS|Remote system time|
|CTimeMS|Corrected system time|
|VX|Velocity X-axis (North-South)|
|VY|Velocity Y-axis (East-West)|
|VZ|Velocity Z-axis (Down-Up)|
|VErr|Velocity estimate error|
|Rst|Velocity reset counter|
|Ign|Ignored|

## WENC
Wheel encoder measurements

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Dist0|First wheel distance travelled|
|Qual0|Quality measurement of Dist0|
|Dist1|Second wheel distance travelled|
|Qual1|Quality measurement of Dist1|

## WINC
Winch

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|Heal|Healthy|
|ThEnd|Reached end of thread|
|Mov|Motor is moving|
|Clut|Clutch is engaged (motor can move freely)|
|Mode|0 is Relaxed, 1 is Position Control, 2 is Rate Control|
|DLen|Desired Length|
|Len|Estimated Length|
|DRate|Desired Rate|
|Tens|Tension on line|
|Vcc|Voltage to Motor|
|Temp|Motor temperature|

## WIND
Windvane readings

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|DrRaw|raw apparent wind direction direct from sensor, in body-frame|
|DrApp|Apparent wind direction, in body-frame|
|DrTru|True wind direction|
|SpdRaw|raw wind speed direct from sensor|
|SpdApp|Apparent wind Speed|
|SpdTru|True wind speed|

## XKF0
EKF3 beacon sensor diagnostics

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|ID|Beacon sensor ID|
|rng|Beacon range|
|innov|Beacon range innovation|
|SIV|sqrt of beacon range innovation variance|
|TR|Beacon range innovation consistency test ratio|
|BPN|Beacon north position|
|BPE|Beacon east position|
|BPD|Beacon down position|
|OFH|High estimate of vertical position offset of beacons rel to EKF origin|
|OFL|Low estimate of vertical position offset of beacons rel to EKF origin|
|OFN|North position of receiver rel to EKF origin|
|OFE|East position of receiver rel to EKF origin|
|OFD|Down position of receiver rel to EKF origin|

## XKF1
EKF3 estimator outputs

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|Roll|Estimated roll|
|Pitch|Estimated pitch|
|Yaw|Estimated yaw|
|VN|Estimated velocity (North component)|
|VE|Estimated velocity (East component)|
|VD|Estimated velocity (Down component)|
|dPD|Filtered derivative of vertical position (down)|
|PN|Estimated distance from origin (North component)|
|PE|Estimated distance from origin (East component)|
|PD|Estimated distance from origin (Down component)|
|GX|Estimated gyro bias, X axis|
|GY|Estimated gyro bias, Y axis|
|GZ|Estimated gyro bias, Z axis|
|OH|Height of origin above WGS-84|

## XKF2
EKF3 estimator secondary outputs

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|AX|Estimated accelerometer X bias|
|AY|Estimated accelerometer Y bias|
|AZ|Estimated accelerometer Z bias|
|VWN|Estimated wind velocity (North component)|
|VWE|Estimated wind velocity (East component)|
|MN|Magnetic field strength (North component)|
|ME|Magnetic field strength (East component)|
|MD|Magnetic field strength (Down component)|
|MX|Magnetic field strength (body X-axis)|
|MY|Magnetic field strength (body Y-axis)|
|MZ|Magnetic field strength (body Z-axis)|
|IDX|Innovation in vehicle drag acceleration (X-axis component)|
|IDY|Innovation in vehicle drag acceleration (Y-axis component)|
|IS|Innovation in vehicle sideslip|

## XKF3
EKF3 innovations

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|IVN|Innovation in velocity (North component)|
|IVE|Innovation in velocity (East component)|
|IVD|Innovation in velocity (Down component)|
|IPN|Innovation in position (North component)|
|IPE|Innovation in position (East component)|
|IPD|Innovation in position (Down component)|
|IMX|Innovation in magnetic field strength (X-axis component)|
|IMY|Innovation in magnetic field strength (Y-axis component)|
|IMZ|Innovation in magnetic field strength (Z-axis component)|
|IYAW|Innovation in vehicle yaw|
|IVT|Innovation in true-airspeed|
|RErr|Accumulated relative error of this core with respect to active primary core|
|ErSc|A consolidated error score where higher numbers are less healthy|

## XKF4
EKF3 variances

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|SV|Square root of the velocity variance|
|SP|Square root of the position variance|
|SH|Square root of the height variance|
|SM|Magnetic field variance|
|SVT|Square root of the total airspeed variance|
|errRP|Filtered error in roll/pitch estimate|
|OFN|Most recent position reset (North component)|
|OFE|Most recent position reset (East component)|
|FS|Filter fault status|
|TS|Filter timeout status bitmask (0:position measurement, 1:velocity measurement, 2:height measurement, 3:magnetometer measurement, 4:airspeed measurement)|
|SS|Filter solution status|
|GPS|Filter GPS status|
|PI|Primary core index|

## XKF5
EKF3 Sensor innovations (primary core) and general dumping ground

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|NI|Normalised flow variance|
|FIX|Optical flow LOS rate vector innovations from the main nav filter (X-axis)|
|FIY|Optical flow LOS rate vector innovations from the main nav filter (Y-axis)|
|AFI|Optical flow LOS rate innovation from terrain offset estimator|
|HAGL|Height above ground level|
|offset|Estimated vertical position of the terrain relative to the nav filter zero datum|
|RI|Range finder innovations|
|rng|Measured range|
|Herr|Filter ground offset state error|
|eAng|Magnitude of angular error|
|eVel|Magnitude of velocity error|
|ePos|Magnitude of position error|

## XKFD
EKF3 Body Frame Odometry errors

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|IX|Innovation in velocity (X-axis)|
|IY|Innovation in velocity (Y-axis)|
|IZ|Innovation in velocity (Z-axis)|
|IVX|Variance in velocity (X-axis)|
|IVY|Variance in velocity (Y-axis)|
|IVZ|Variance in velocity (Z-axis)|

## XKFM
EKF3 diagnostic data for on-ground-and-not-moving check

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this message instance applies to|
|OGNM|True of on ground and not moving|
|GLR|Gyroscope length ratio|
|ALR|Accelerometer length ratio|
|GDR|Gyroscope rate of change ratio|
|ADR|Accelerometer rate of change ratio|

## XKFS
EKF3 sensor selection

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|MI|compass selection index|
|BI|barometer selection index|
|GI|GPS selection index|
|AI|airspeed selection index|

## XKQ
EKF3 quaternion defining the rotation from NED to XYZ (autopilot) axes

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|Q1|Quaternion a term|
|Q2|Quaternion b term|
|Q3|Quaternion c term|
|Q4|Quaternion d term|

## XKT
EKF3 timing information

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this message instance applies to|
|Cnt|count of samples used to create this message|
|IMUMin|smallest IMU sample interval|
|IMUMax|largest IMU sample interval|
|EKFMin|low-passed achieved average time step rate for the EKF (minimum)|
|EKFMax|low-passed achieved average time step rate for the EKF (maximum)|
|AngMin|accumulated measurement time interval for the delta angle (minimum)|
|AngMax|accumulated measurement time interval for the delta angle (maximum)|
|VMin|accumulated measurement time interval for the delta velocity (minimum)|
|VMax|accumulated measurement time interval for the delta velocity (maximum)|

## XKTV
EKF3 Yaw Estimator States

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|TVS|Tilt Error Variance from symbolic equations (rad^2)|
|TVD|Tilt Error Variance from difference method (rad^2)|

## XKV1
EKF3 State variances (primary core)

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|V00|Variance for state 0|
|V01|Variance for state 1|
|V02|Variance for state 2|
|V03|Variance for state 3|
|V04|Variance for state 4|
|V05|Variance for state 5|
|V06|Variance for state 6|
|V07|Variance for state 7|
|V08|Variance for state 8|
|V09|Variance for state 9|
|V10|Variance for state 10|
|V11|Variance for state 11|

## XKV2
more EKF3 State Variances (primary core)

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF3 core this data is for|
|V12|Variance for state 12|
|V13|Variance for state 13|
|V14|Variance for state 14|
|V15|Variance for state 15|
|V16|Variance for state 16|
|V17|Variance for state 17|
|V18|Variance for state 18|
|V19|Variance for state 19|
|V20|Variance for state 20|
|V21|Variance for state 21|
|V22|Variance for state 22|
|V23|Variance for state 23|

## XKY0
EKF Yaw Estimator States

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this data is for|
|YC|GSF yaw estimate (rad)|
|YCS|GSF yaw estimate 1-Sigma uncertainty (rad)|
|Y0|Yaw estimate from individual EKF filter 0 (rad)|
|Y1|Yaw estimate from individual EKF filter 1 (rad)|
|Y2|Yaw estimate from individual EKF filter 2 (rad)|
|Y3|Yaw estimate from individual EKF filter 3 (rad)|
|Y4|Yaw estimate from individual EKF filter 4 (rad)|
|W0|Weighting applied to yaw estimate from individual EKF filter 0|
|W1|Weighting applied to yaw estimate from individual EKF filter 1|
|W2|Weighting applied to yaw estimate from individual EKF filter 2|
|W3|Weighting applied to yaw estimate from individual EKF filter 3|
|W4|Weighting applied to yaw estimate from individual EKF filter 4|

## XKY1
EKF Yaw Estimator Innovations

|FieldName|Description|
|---|---|
|TimeUS|Time since system startup|
|C|EKF core this data is for|
|IVN0|North velocity innovation from individual EKF filter 0 (m/s)|
|IVN1|North velocity innovation from individual EKF filter 1 (m/s)|
|IVN2|North velocity innovation from individual EKF filter 2 (m/s)|
|IVN3|North velocity innovation from individual EKF filter 3 (m/s)|
|IVN4|North velocity innovation from individual EKF filter 4 (m/s)|
|IVE0|East velocity innovation from individual EKF filter 0 (m/s)|
|IVE1|East velocity innovation from individual EKF filter 1 (m/s)|
|IVE2|East velocity innovation from individual EKF filter 2 (m/s)|
|IVE3|East velocity innovation from individual EKF filter 3 (m/s)|
|IVE4|East velocity innovation from individual EKF filter 4 (m/s)|


