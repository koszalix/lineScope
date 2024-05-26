# Index
1. [Overview](#Overview)
2. [Key features](#key_features)
3. [Specification](#specification)
4. [Modules](#construction)
  - [Voltage probe](#voltage_probe)
  - [0.5A probe](#05A_probe)
  - [5A probe](#5A_probe)
  - [Relay board](#relay_board)
  - [Isolators](#isolators)
5. [Mechanical constructions](#Mechanical_construction)  
6. [Bringup](#Bringup)
# Overview 

lineScope is an oscilloscope attachment for  safe measurement of AC lines. Two current ranges (0.5A/5A) and one voltage range (260V) are supported. 

The lineScope construction is fully modular, so range can be change easily just by change of sense module. 

# Key Features 
- Separate socket for `DUT` power and devices power 
- `260V` Voltage measurement range 
- `0.5A` and `5A` current measurement range 
- Overvoltage and overcurrent protection
- Switchable output 
- `BNC` connectors for easy oscilloscope connection 

# Specification

## Voltage measurement
- Measurement range `260V`
- `DUT` voltage to output voltage ratio 1mV/V
- Output noise level `<2mV`
- Frequency response 10Hz - 10kHz<!-- Need to be checked against real device-->
- Dielectric strength `2kV 1min`
- Linearity `<1%`
- Uncertainty `<5%`

## Current measurement
- Measurement range `5A` or `0.5A`
- `DUT` current to output voltage `1 mA/mV` for `0.5A` range; `10 mA/mV` for `5A` range
- Output noise level `<2mV`
- Frequency response 10Hz - 10kHz<!-- Need to be checked against real device-->
- Dielectric strength `2kV 1min`
- Linearity `<1%`
- Uncertainty `<5%`

## Operating conditions 
- Temperature `15-35`
- Humidity `20-70 RH`

# Modules
Construction of the `lineScope` is fully modular, for basic operation only `Voltage probe`, `Isolators`  and `0.5A probe` or `5A probe` is  required. 
However it's recommended to have full setup with `Relay board` and two current probes.  Connections between modules are presented at diagram bellow.

## Voltage probe
### General description
The voltage probe transform 230V AC line voltage into mV range with galvanic separation. Voltage transformation is done by TV19G current transformer, connected in series with known resistance (150k) into AC line.
### Input protection
Input of AC line  is protected by 600Vrms GDT and 275Vrms MOX, however is highly recommended to use  proper surge protection power cord. 

### Input voltage range
The board is designed for 230V AC line input however any voltage from 1V to 260Vrms should work. 

The probe should be connected parallel to AC line. 

### Output voltage range
Output voltage is proportional to input voltage, the ratio is equal to 1:1000 (1mV/V). Maximum output voltage should not exceed 300mV range.

### Single ended or differential output

By default board output is single ended, however pcb can be switched to differential output, to switch pcb to differential output the `R4` resistor must be removed and `RV2, DZ3, DZ4` should be mounted. 

### Connectors 
Board is equipped with pass trough connectors for both line and neutral. Standard 2.54mm pin headers are used for the output connector, pinout table is presented bellow.

| Designator | Pin | Description                               |
| ---------- | --- | ----------------------------------------- |
| J1         | 1   | AC Line - Phase                           |
| J3         | 1   | AC Line - Phase                           |
| J2         | 1   | AC Line - Neutral                         |
| J4         | 1   | AC Line - Neutral                         |
| J5         | 1   | SE output \| Differential output positive |
| J5         | 2   | GND                                       |
| J5         | 3   | GND \| Differential output negative       |
## 0.5A probe
### Overview 
The 0.5A probe is current probe, designed to transform current into voltage, the nominal measured current is 0.5A and output voltage is 1.5V maximum. 

### Input current range and protection
The rated probe current is 0.5A, current larger than 0.5A can permanently destroy the the PCB, or cause dielectric breakdown. 

The probe should be connected in series with load.

AC Input is protected only by 5x20mm 500mA ceramic fuse, keep in mind that 5x20 fuses can only work up to 250V, if you plan to work with higher voltages you should consider board modification. 

### Output voltage 
The output voltage is proportional to input current, with 1:3 ratio (3mV/mA). Maximum output voltage should not exceed 1.5Vrms for nominal probe current(0.5A) 

### Single ended or differential output

By default board output is single ended, however pcb can be switched to differential output, to switch pcb to differential output the `R2` resistor must be removed and `RV2, DZ3, DZ4` should be mounted. 

# Connectors 

Board is equipped with 3 AC line connectors, and one standard 90 degree 2,54mm pin headers for output. 

Connectors pinout is presented at table bellow. 

| Designator | Pin | Description                                |
| ---------- | --- | ------------------------------------------ |
| J1         | 1   | AC Line input                              |
| J3         | 1   | AC Line pass trough                        |
| J2         | 1   | AC Line output                             |
| J4         | 1   | SE output \| Differential output possitive |
| J4         | 2   | GND                                        |
| J4         | 3   | GND \| Differential output negative        |
## 5A probe
### Overview
The 5A probe is current probe, designed to transform current into voltage, the nominal measured current is 5A and output voltage is 1.5V maximum. 

### Input current range and protection
The rated probe current is 5A, current larger than 5A can permanently destroy the the PCB, or cause dielectric breakdown. 

The probe should be connected in series with load.

AC Input is protected only by 5x20mm 5A ceramic fuse, keep in mind that 5x20 fuses can only work up to 250V, if you plan to work with higher voltages you should consider board modification. 

###  Output voltage 
The output voltage is proportional to input current, with 1:300 ratio (300mV/A). Maximum output voltage should not exceed 1.5Vrms for nominal probe current(5A).

### Single ended or differential output

By default board output is single ended, however pcb can be switched to differential output, to switch pcb to differential output the `R4` resistor must be removed and `RV2, DZ3, DZ4` should be mounted. 

### Connectors 

Board is equipped with 3 AC line connectors, and one standard 90 degree 2,54mm pin headers for output. 

Connectors pinout is presented at table bellow. 

| Designator | Pin | Description                                |
| ---------- | --- | ------------------------------------------ |
| J1         | 1   | AC Line input                              |
| J3         | 1   | AC Line pass trough                        |
| J2         | 1   | AC Line output                             |
| J4         | 1   | SE output \| Differential output possitive |
| J4         | 2   | GND                                        |
| J4         | 3   | GND \| Differential output negative        |
## Relay board
### Overview 
The relay board is designed for selecting current probes and switching the output, for output switching both line and neutral is switched off. 

### Switching capability 
All relays, tracks and connectors are rated for `16A/250V` AC line switching. 

### Relay board
All relays are mounted in standard 7.5mm relays sockets, to change faulty relay no soldering is required.  

Relays coils are rated for 12V DC, back emf diodes are present on the PCB. 

The `Relpol RM85-1011-35-2012` are used, but any `16A` rated, `12V` coil relay can be used for replacemnt
### Connectors 

For HV standard 6.3mm tab connectors are used, for low voltage/control JST-XH connectors are used. 

Connectors pinout at presented in table bellow

| Designator | Pin | Description            |
| ---------- | --- | ---------------------- |
| J1         | 1   | Neutral in             |
| J3         | 1   | Neutral out            |
| J2         | 1   | Line out               |
| J4         | 1   | Line high current in   |
| J6         | 1   | Line low current in    |
| J5         | 1   | VCC                    |
| J5         | 2   | Line `ON/OFF`          |
| J5         | 3   | Range selection        |
| J5         | 4   | Neutral `ON/OFF`       |
| J5         | 5   | GND                    |
| J7         | 1   | AC Power (low voltage) |
| J7         | 2   | AC Power (low voltage) |
## Isolator board

### Overview 
The `Isolator board` is designed as carrier board for  the probes modules and as second layer of galvanic isolation. 

### Connecting the probes
Voltage probe must be connected to the `J3` connector, current probes must be connected to `J4` and `J5` connectors. 

### Connectors 

| Designator | Pin | Description               |     |
| ---------- | --- | ------------------------- | --- |
| J1         | 1   | AC power grid side        |     |
| J1         | 2   | AC power grid side        |     |
| J2         | 1   | AC power scope side       |     |
| J2         | 2   | AC power scope side       |     |
| J3         | 1   | Voltage probe signal      |     |
| J3         | 2   | Voltage probe GND         |     |
| J3         | 3   | Voltage probe GND         |     |
| J4         | 1   | Current probe signal      |     |
| J4         | 2   | Current probe GND         |     |
| J4         | 3   | Current probe GND         |     |
| J5         | 1   | Current probe signal      |     |
| J5         | 2   | Current probe GND         |     |
| J5         | 3   | Current probe GND         |     |
| J7         | 1   | Voltage output hot        |     |
| J7         | 2   | Voltage output cold       |     |
| J8         | 1   | Current output hot        |     |
| J8         | 2   | Current output cold       |     |
| J9         | 1   | VCC2                      |     |
| J9         | 2   | Select probe low current  |     |
| J9         | 3   | Select probe high current |     |
| J9         | 4   | GND                       |     |

# Mechanical Construction 

# Bringup

Bringup was descried [[Bringup | here]] 










































































































































































































