# Gyro Glove Controlled Vehicle with Signal Loss Sound Alert

[![Releases](https://img.shields.io/badge/Releases-Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert-4A90E2?style=for-the-badge&logo=github)](https://github.com/Mfa565/Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert/releases)

![Arduino Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Arduino-Logo.png/320px-Arduino-Logo.png)

Table of Contents
- About this project
- Why this project exists
- What you get
- How it works
- Hardware components
- Software architecture
- Data structures and algorithms
- Getting started
- Building and running
- How to test
- Usage scenarios
- Project structure
- Documentation and diagrams
- Hardware and firmware interfaces
- Debugging and troubleshooting
- Maintenance and future work
- Contributing
- Licensing
- Acknowledgements
- References

About this project
This repository houses the code and documentation for a gyro glove controlled vehicle that detects signal loss and emits an audible alert. The work was completed as part of the Control Systems Technology course of my Master’s Degree in Computer Science and Engineering at the University of Catania. The project blends elements of robotics, control systems, embedded programming, and data structures to deliver a compact, demonstrable system that responds to user input via a glove-mounted inertial measurement unit (IMU) and provides a clear alert when control signals are lost.

Why this project exists
- Demonstrate closed-loop control ideas on a small scale vehicle.
- Explore sensor fusion concepts using a wearable IMU as the input device.
- Provide a robust signal-loss alert that helps ensure safety in semi-autonomous operations.
- Exercise software engineering practices in embedded environments, including debugging and test strategies.

What you get
- A working firmware framework for a glove-based control interface.
- A vehicle control loop that translates glove motion into vehicle commands.
- A signal loss detector that triggers a sound alert when control input is interrupted.
- A modular codebase designed for extensions, tests, and improvements.
- Documentation that covers hardware, software, and usage.

How it works
- The glove carries an IMU that streams orientation and motion data to a microcontroller.
- The vehicle runs a simple motor-driving loop that interprets control signals as speed and steering commands.
- A watchdog mechanism monitors the integrity of the control link. If the signal fails or becomes unstable, the system switches to a safe mode and sounds an alert.
- The alert is produced by a buzzer or speaker connected to the microcontroller, providing an immediate audible cue.

Design goals
- Clarity: straightforward code paths and readable comments.
- Portability: components chosen to fit common Arduino-compatible hardware.
- Robustness: simple fail-safes for signal loss and sensor glitches.
- Extensibility: clean separation between glove-side input handling and vehicle-side actuation.

Emojis to guide you through the journey
- 🧰 Hardware-first approach
- 🧭 Clear control flow
- 🔊 Audible alerts for safety
- 🧪 Thorough testing and debugging
- 🧭 Roadmap for future improvements

Hardware components (typical)
Note: The exact parts can vary. This list reflects common choices for a glove-to-vehicle control setup.

- Arduino-compatible microcontroller (Uno, Mega, or compatible)
- Inertial Measurement Unit (IMU) sensor (e.g., MPU-6050, ICM-20689)
- Motor driver module (e.g., L298N or A4988/DRV8825 for stepper systems)
- DC motors or a small rover chassis
- Buzzer or small speaker for the signal loss alert
- Bluetooth, RF, or other short-range wireless module for the control link (optional, depending on your glove-to-vehicle interface)
- Power supply for the vehicle (battery pack appropriate for the motor driver and motors)
- Miscellaneous: wires, breadboard or PCB, voltage regulators, resistors, capacitors

If you want to inspect the release assets directly, you can check the Releases page:
- Link to releases: https://github.com/Mfa565/Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert/releases

Software architecture
- Firmware layer (Arduino/C++): Reads IMU data, processes motion, maps to vehicle commands, and drives motors. It also monitors the control link for integrity and triggers the alert on signal loss.
- Input handling module: Interfaces with the glove IMU, performs calibration, filters noise, and converts motion into a control signal.
- Control loop: A simple proportional-like controller that translates orientation and motion into motor commands. It includes a safety check for signal loss.
- Sound alert module: Produces the audible alert when signal loss is detected.
- Logging and debugging: Lightweight logging with timestamps or event markers to help trace behavior during testing.
- Data structures: State enums for vehicle mode, signal status, and calibration state; lightweight buffers for IMU data.

Data structures and algorithms
- State management
  - VehicleState: {IDLE, ACTIVE, SAFETY}
  - SignalStatus: {OK, WARNING, LOST}
  - CalibrationPhase: {NOT_CALIBRATED, CALIBRATING, CALIBRATED}
- Control signal processing
  - Input normalization: Raw IMU data to a normalized command range
  - Dead zones: Small motions do not produce vehicle commands
  - Smoothing: Simple moving average to reduce jitter
- Signal loss detection
  - Watchdog timer: Detects if IMU data or control link fails to update within a threshold
  - Threshold checks: If data rate or message integrity falls below threshold, switch to LOST
  - Fail-safe: Bring vehicle to a safe stop or slow descent into a controlled idle
- Sound alert design
  - Audible cue pattern to denote signal loss state
  - Repeat until signal is restored or reset

Getting started
- Prerequisites
  - A computer with Arduino IDE or PlatformIO
  - Basic knowledge of Arduino programming and C/C++
  - A working glove prototype with IMU and a compatible wireless link
  - A small vehicle chassis with motors and a driver
- Quick setup steps
  - Install the Arduino IDE
  - Install necessary board definitions for your MCU
  - Connect the glove and vehicle hardware as described in the hardware section
  - Open the firmware project in the IDE
  - Configure board, port, and any project-specific settings
  - Compile and upload to the glove’s microcontroller
  - Upload or pair the vehicle firmware if needed
  - Power on the system and verify the control path and alert behavior

Building and running
- How to build
  - Ensure all libraries used by the firmware are present (IMU library, motor control library, communication library)
  - Choose the correct board and port in the IDE
  - Build the project to verify there are no compile errors
- How to run
  - Power the glove and vehicle
  - Calibrate the glove on startup if your workflow requires calibration
  - Move the glove to test vehicle response
  - If the control link is interrupted, listen for the alert and observe vehicle behavior
- Firmware organization
  - glove_input/ or input_drivers/ for IMU handling
  - vehicle_control/ for motor driving logic
  - safety/ for signal loss and fail-safe behavior
  - audio/ for buzzers and alert tones
  - tests/ for unit tests and test scenarios

How to test
- Unit tests (where possible)
  - Test IMU data parsing with synthetic inputs
  - Test mapping from IMU movement to motor commands
  - Test the watchdog timer with simulated signal loss
- Integration tests
  - Connect glove to vehicle and verify the end-to-end control loop
  - Simulate signal loss and verify audible alert triggers
  - Validate safe stop behavior when input becomes invalid
- Manual tests
  - Calibrate the glove and verify consistent responses
  - Check response to rapid glove motions and ensure no erratic motor commands
  - Confirm that the alert resumes once the signal is restored

Usage scenarios
- Classroom demonstration
  - A simple demonstration of glove-based control with a clear signal loss alert
  - Suitable for a control systems lecture or a robotics showcase
- Research setup
  - A starting point for experiments in wearable control or human-machine interaction
  - Extendable to add more sensors or refine the control algorithm
- Hobby project
  - A fun platform to learn embedded programming, motor control, and audio signaling
  - A base for customizing the vehicle’s motion profile and alert behavior

Project structure
- docs/
  - Design notes, diagrams, and experimental results
  - Calibration procedures and testing logs
- firmware/
  - Arduino sketches and related source files
  - Subfolders for input, control, safety, and audio modules
- hardware/
  - Bill of Materials (BOM)
  - Wiring diagrams
  - Assembly instructions
- examples/
  - Sample configurations for different hardware setups
- tests/
  - Test scripts and mock data
- tools/
  - Utility scripts for data collection and device flashing
- LICENSE
  - License details

Documentation and diagrams
- System diagram
  - Shows the glove IMU, communication link, and vehicle control loop
- Signal flow diagram
  - Captures data path from glove to vehicle and the response to signal loss
- Calibration guide
  - Step-by-step procedure to calibrate the IMU for stable control
- Wiring diagrams
  - Clear connection maps for the glove sensors and the motor driver
- Software architecture diagram
  - High-level view of modules and their interactions

Hardware and firmware interfaces
- Glove interface
  - IMU data stream format (e.g., orientation, angular velocity)
  - Optional calibration data for smoothing and dead zones
- Vehicle interface
  - PWM or control signals to motor drivers
  - Feedback lines if available (e.g., motor encoder data)
- Sound alert interface
  - Buzzer control pin and alert tone pattern
- Communication interface
  - Wireless channel (e.g., Bluetooth, RF) with a simple handshake and data rate

Debugging and troubleshooting
- Common issues
  - IMU not initializing correctly
  - No movement response when glove is moved
  - Unexpected motor behavior or jitter
  - Alert not sounding on signal loss
- Debug tips
  - Use serial output to log IMU data and command values
  - Validate calibration data and apply smoothing as needed
  - Check wiring for loose connections, especially power lines
  - Confirm motor driver configuration (microstepping, currents)
- Quick fixes
  - Recalibrate the glove if the mapping drifts
  - Increase or decrease dead zones to fit your motion profile
  - Adjust the watchdog timeout to balance responsiveness and noise tolerance

Maintenance and future work
- Maintenance plan
  - Regular updates to firmware and libraries
  - Periodic calibration checks
  - Routine testing with the latest hardware revisions
- Possible enhancements
  - Add more sensor modalities (e.g., flex sensors on the glove)
  - Implement advanced filtering (Kalman or complementary filter)
  - Expand the communication link for longer range
  - Add a graphical user interface to monitor behavior
- Roadmap ideas
  - Introduce a fallback control mode when the glove is not available
  - Support multiple glove users with profile-based calibration
  - Integrate with a simulation environment for testing without hardware

Contributing
- How to contribute
  - Open issues for bugs and feature requests
  - Submit pull requests with focused changes
  - Include tests and clear explanations of the changes
- Coding standards
  - Use clear variable names and simple logic
  - Document non-obvious decisions
  - Keep functions short and focused
- Review process
  - Maintainers will review for correctness, safety, and clarity
  - Expect feedback and be prepared to revise

License
- This project is released under the MIT License.
- A copy of the license is provided in the repository.

Acknowledgements
- This work was completed as part of the Control Systems Technology course of my Master’s Degree in Computer Science and Engineering at the University of Catania.
- Thanks to instructors and peers who provided feedback, and to the open-source community for the tools and libraries that made this project possible.

Releases
- Release assets and official binaries are available on the Releases page. From that page, download the appropriate asset and execute it according to the included instructions. The Releases page can be found here: https://github.com/Mfa565/Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert/releases

References
- Arduino official documentation
- IMU sensor datasheets and tutorials
- Motor driver manuals and wiring guides
- Control systems textbooks and lecture notes from the University of Catania

Note: For the Releases page, a path is included in the URL, pointing to a page that lists downloadable assets. On that page you will find the files to download and execute. If you encounter any issues with the links or assets, check the Releases section for the latest updates and instructions. The link is provided again here for convenience: https://github.com/Mfa565/Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert/releases.