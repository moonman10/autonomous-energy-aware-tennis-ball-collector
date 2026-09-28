# Project Definition: Autonomous Energy-Aware Tennis Ball Collector

## Purpose

Design, build, and validate a low-voltage autonomous mobile robot that detects and collects tennis balls from a defined court or controlled test area. The project combines EV power-system integration, embedded control, mechanical design, CAN communication, computer vision, and ROS 2 robotics in one testable platform.

## Year 1 Definition of Done

The project is complete when the rover can:

1. Navigate at low speed within a defined test area using LiDAR, IMU, wheel encoders, and ROS 2.
2. Detect tennis balls using a camera-based perception system and select collection targets.
3. Drive to a detected ball, collect it through a front intake, and store it in an onboard hopper.
4. Monitor battery voltage, current, temperature, and smart-BMS status.
5. Communicate mission, battery, motor, thermal, and fault data over CAN.
6. Log data and safely enter a Derated or Fault state when predefined limits are reached.

## Safety Boundaries

- Low-voltage propulsion system
- Purchased smart BMS with independent cell protection and balancing
- Main fuse, emergency stop, service disconnect, and protected power distribution
- Low-speed operation in a controlled test area
- Initial operation around people only under direct supervision
- Battery thermal validation performed with a heater-based test module rather than intentional heating of propulsion cells

## Major Subsystems

| Subsystem | Function |
|---|---|
| Chassis and drivetrain | Differential-drive chassis, geared motors, encoders, wheels, and protective bumper |
| Ball collection system | Front funnel/intake, low-voltage intake actuator, ball-presence sensing, and removable hopper |
| Battery and power system | Battery pack, purchased smart BMS, fuse, emergency stop, service disconnect, power distribution, and DC-DC conversion |
| STM32 VCU | Real-time motor control, sensor acquisition, safety-state logic, intake control, CAN telemetry, and fault response |
| Raspberry Pi and ROS 2 | LiDAR/IMU integration, camera processing, localization, navigation, coverage planning, and collection mission logic |
| Perception system | Camera-based tennis-ball detection; LiDAR remains the primary navigation and obstacle-detection sensor |
| Thermal test module | Heater, fan, and temperature sensors used to validate monitoring, fan control, and power derating |
| Data and validation | CAN logs, mission logs, energy/thermal analysis, test plans, fault injection, and MATLAB/Simulink comparison |

## Architecture Principle

The BMS protects individual cells. The STM32 VCU protects rover operation. The Raspberry Pi decides how to complete the collection mission. Each layer has a distinct responsibility, so a high-level software failure cannot remove cell-level battery protection.

## Explicitly Deferred Features

- Autonomous charging dock
- Regenerative braking hardware
- Custom BLDC inverter
- Liquid-cooling loop
- Custom propulsion BMS
- Fully autonomous hopper emptying

## Professional Summary

This project develops an autonomous tennis-ball collection robot that integrates battery-system supervision, embedded motor control, CAN communication, ROS 2 navigation, camera-based object detection, and a custom ball-intake mechanism. The platform is designed to make energy-aware operating decisions, log system behavior, and transition safely to derated or fault states when electrical or thermal limits are approached.
