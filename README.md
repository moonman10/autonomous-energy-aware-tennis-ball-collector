Autonomous Energy-Aware Tennis Ball Collector

An in-development low-voltage autonomous mobile robot that collects tennis balls from a defined court or test area. The platform combines electric-vehicle power-system monitoring, embedded control, CAN communication, ROS 2 navigation, camera-based ball detection, and a custom mechanical collection mechanism.

The collector is designed to navigate safely at low speed, locate tennis balls, drive to collection targets, intake balls into an onboard hopper, and monitor its own energy, temperature, and fault state throughout the mission. A primary engineering goal is to make the system aware of its electrical condition: it should reduce performance or stop safely before a battery-protection event occurs.

Core Capabilities
- Navigate through a defined court or test area using LiDAR, IMU, wheel encoders, and ROS 2
- Detect tennis balls with a camera-based perception pipeline
- Collect balls using a front intake and onboard storage hopper
- Measure battery voltage, current, temperature, and BMS fault status
- Exchange battery, motor, thermal, and mission data over CAN
- Apply low-speed safety states: Ready, Running, Derated, and Fault
- Log mission, energy, and fault data for test analysis

System Overview

The Raspberry Pi runs ROS 2 navigation, camera processing, coverage/collection planning, and high-level mission logic. An STM32-based Vehicle Control Unit (VCU) handles real-time sensor acquisition, motor control, safety-state logic, CAN telemetry, and commands to the intake mechanism. A purchased smart BMS remains responsible for independent cell-level protection and balancing.
See [Project Definition](docs/project_definition.md) and [System Architecture](docs/system_architecture.md).

Year 1 Scope Boundary

The Year 1 target is a low-voltage, low-speed collector that autonomously navigates a controlled test area and collects tennis balls into an onboard hopper while monitoring energy and safety status. Autonomous charging, regenerative braking, a custom inverter, liquid cooling, and a custom propulsion BMS are intentionally out of scope.
