#GRX-CI-RS232, GRX-CI-NWK-E, GRX-IA-CI-RS232, and GRX-IA-CI-NWK-E 
## Control Interfaces

#Overview

##Description
Up to eight GRAFIK Eye Control Units can be interfaced with your personal computer or auxiliary audio/visual equipment via TCP/IP communication over Ethernet (GRX-CI-NWK-E) or RS232 (GRX-CIRS232). The interface can be used to execute Control Commands and allow for Status Monitoring.

##Reference Documents
- GRAFIK Eye Control Unit Installation Guide

##Control Commands
The Control Interface can send commands from a PC or A/V equipment to a maximum of eight GRAFIK Eye Control Units. The following commands are available:
**Select Scene**: Select any scene on any GRAFIK Eye Control Unit.
**Scene Lock**: Prevent changes to GRAFIK Eye Control Unit(s) from any remote location.
**Request Scene Status**: Request the current scene of every GRAFIK Eye Control Unit in the system.
**Read Zone Intensity**: Read the zone intensities on a specified GRAFIK Eye Control Unit.
**Set Zone Intensity** *(requires 3500/4500 Series Control Unit)*: Change the intensities of the given zones on a specified GRAFIK Eye 3500 or 4500 Series Control Unit in the given fade time.
**Sequence**: Begin sequencing scenes 1 to 4 or 5 to 16 (DIP-switch selectable) on selected GRAFIK Eye Control Unit(s).
**Zone Lock**: Prevent permanent changes to preset levels of GRAFIK Eye Control Unit(s).
**Zone Raise/Lower**: Raise or lower any zone on any GRAFIK Eye Control Unit.

Refer to the GRAFIK Eye RS232 Protocol and Command Set on the enclosed CD for detailed command descriptions and information on configuring your PC or auxiliary A/V equipment for use with Lutron’s RS232 interfaces.

##Status Monitoring
The Control Interface will allow a PC or auxiliary A/V equipment to monitor a GRAFIK Eye system. The following notifications are available:
**Raw Feedback** *(DIP switch 6 ON)*: Report all button presses and releases on all GRAFIK Eye Control Units and Accessory Controls.
**Scene Status** *(DIP switch 7 ON)* Report scene status changes on all GRAFIK Eye Control Units. Scene status may be changed by Control Units, Accessory Controls, or sequences.

#Communication Settings: 
##NWK-E
To configure your device to talk to the GRAFIK Eye Ethernet Interface, open a Telnet session with the following default IP address, port, and login information:
- Default IP Address: 192.168.250.1
- Default Port: 23 (Telnet Port)
- Default Login for Connection 1: ‘nwk’
- Default Login for Connection 2: ‘nwk2’
If you wish to send these commands from a PC, run the Microsoft® Windows® Telnet program or an equivalent program.

##RS232
To configure your device to talk to the GRAFIK Eye RS232 Interface, use the data conventions listed below.
- 9600 BAUD
- 8 DATA BITS
- 1 STOP BIT
- NO PARITY
If you wish to send these commands from a PC, run the Microsoft® Windows® Hyper Terminal program or an equivalent program. Then, select Local Echo, Line Feed, and Carriage Return inbound and outbound. This allows you to see the characters that you are typing as well as keep the responses from overwriting typed characters.

#Configuration Options
The settings of the Control Unit are configured via a set of five DIP switches. These settings affect the interface operation between GRAFIK Eye Control Units and your PC or auxiliary A/V equipment. Control Units and Accessory Controls must be uniquely addressed for use with the Control Interface. For addressing, see the GRAFIK Eye Installation Guide included with the Control Units. The Control Interface will default to address 16, unless addressed in fixed address mode (see below). 

The DIP switches apply as follows:

| Switch | Function               | ON Setting                                         | OFF Setting                         |
|----------------------------------------------------------------------------------------------------------------------------|
| 1      | Zone Lock Retain       | Retains zone lock settings after power cycle       | Zone lock off after power cycle     |
| 2      | Scene Lock Retain      | Retains scene lock settings after power cycle      | Scene lock off after power cycle    |
| 3      | Sequence Retain        | Retains sequence mode settings after power cycle   | Sequence mode off after power cycle |
| 4      | Sequence Type          | Sequences through scenes 1-4                       | Sequences through scenes 5-16       |
| 5      | Fixed Address          | Use switches 1-4 to set unit address (see below)   | Switches 1-4 have normal function   |
| 6      | Raw Feedback           | Report all button presses (see below)              | Do not report button press events   |
| 7      | Scene Status           | Report all 8 data link scene status upon new scene | Do not report scene status events   |
| 8      | *Not Used*             |                                                    |                                     |

##Zone Lock Retain, Scene Lock Retain and Sequence Retain
- Switches 1-3
In the event of a power outage, the Control Interface will retain which GRAFIK Eye Control Units were in Zone Lock, Scene Lock, and Sequence modes (set using the Control Interface), respectively. Upon returning power, Control Units that had been in Zone Lock, Scene Lock, or Sequence mode (set using the Control Interface) will stay locked or sequencing if the DIP switches are in the ON position. When these DIP switches are in the OFF position, this information will not be restored upon power up. 
*These DIP switches do not affect Zone Lock, Scene Lock, or Sequence mode set by a GRX-AV in 4Q mode.*

##Sequence Type
- Switch 4
Set the scene range that GRAFIK Eye Control Units will sequence using the SEQUENCE command. In the OFF position, GRAFIK Eye Control Units will sequence scenes 1 to 4. In the ON position, they will sequence scenes 5 to 16.

##Fixed Addressing
- Switch 5, then 1-4
*Note*: This option affects the other configuration options, see below.
If you want to add a Control Interface to a Data Link that already has a GRXCI-NWK-E, GRX-CI-RS232 or GRX-CI-PRG, the fixed address option must be used by setting DIP Switch 5 ON. DIP Switches 1 to 4 are then used to address the Interface. Refer to the addressing table.

The Sequence Type (DIP switch 4) that will run when using the SEQUENCE command of the Control Interface is determined by the address of the Control Interface. Even addresses (2, 4, etc.) will sequence scenes 1 to 4, and odd addresses (1, 3, etc.) will sequence scenes 5 to 16.

A fixed address Control Interface can only do one of the following modes at any time: Zone Lock (ZL), Scene Lock (SL), or Sequence (SQ).
**Note**: Use the fixed address option only if there is a GRX-CI-PRG, GRX-CI-RS232, or GRX-CI-NWK-E already on the Data Link. Otherwise, the default address is 16.

##Raw Feedback
- Switch 6
Setting DIP switch 6 of the Control Interface in the ON position will report when a button has been pushed or released on a GRAFIK Eye Control Unit or Accessory Control. This is described further in a later section.