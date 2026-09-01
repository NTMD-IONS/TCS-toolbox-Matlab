# Library of functions to control TCS device

## Note
Two Classes have been built:
- "serial_manager": to manage the serial communication (USB) between the computer and the TCS device,
- "tcs_initialize": to control the TCS device using its specific commands.

"tcs_initialize" is built on top of "serial_manager", and inherits Properties (variables) and Methods (functions) from it.

## General use

### Initialization : create the object using the class constructor, find COM port and 
ClassName is "tcs_initialize", the name of the built object can be chosen freely\
for example:
- tcs = tcs_initialize;\
This can be done for each TCS device ("tcs1", "tcs2", etc.) if several are connected to the same computer.\
In this case, connect one TCS device to the computer, call "obj1 = tcs_initialize;",\
then connect the second TCS device and call "obj2 = tcs_initialize;", etc.

### Use methods for serial communication and TCS control
It is advised to wait for at least 1 ms between successive commands: "WaitSecs(0.001)" using Psychtoolbox; or "pause(0.001)" using a native Matlab function.\
Once the object, "tcs" in the previous section, has been created, methods associated to it can be called:
- obj.MethodName;

for example to close the serial communication:
- tcs.delete;

for example to read the data from the serial port:
- tcs.receive;

### Call any function (methods) or variables (properties) associated with the "tcs" object
Examples:
- tcs.disable_temperature_feedback;\
to disable the reading of the temperature
- tcs.set_neutral_temperature(30);\
to set the neutral temperature to 30°C
- tcs.set_active_zones(zones);\
with zones = 01110; to activate zones 2,3,4
- tcs.enable_temperature_feedback(freq);\
with freq = 100; to enable the reading of the temperature at 100 Hz, during stimulation
- battery_level = tcs.get_battery;\
to retrieve the voltage and percentage of charge of the TCS device and store them in "battery_level".

Variables (Properties) shared across classes can be called the same way:
- tcs.portName
>> 'COM6'
- tcs.verbosity
>> 1

## Get help about functions and variables

### List the properties of the class
Variables that are implicitly shared across classes can be listed by:
- properties ClassName\
for example:
- properties tcs_initialize\
or
- properties('tcs_initialize')\
or, if an object has already been created:
- properties(obj)

### List the methods of the Class 'tcs_initialize'
Functions or methods that are implicitly shared across classes can be listed by:
- methods('ClassName')\
for example:
- methods('tcs_initialize')\
or
- methods tcs_initialize\
or, if an object has already been created:
- methods(obj)

### Get help about a specific method
- help ClassName.MethodName\
for example:
- help tcs_initialize.get_battery

#### Created with MATLAB (R2024a) with Psychtoolbox (3-3.0.19.7) on Windows 11 (25H2).
- Author : Cédric Lenoir, Neuroscience Techniques and Methods Developement Platform (NeTMeD),
% Email : cedric.lenoir@uclouvain.be
% Institute of Neuroscience (IoNS), UCLouvain, Brussels, Belgium.
% Version 4.0.0, August 2026.//
