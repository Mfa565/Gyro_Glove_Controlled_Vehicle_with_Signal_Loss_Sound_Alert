# Gyro Glove Controlled Vehicle with Signal Loss Sound Alert

## 📚 Introduction

My name is **Stefano Caramagno**, and I'm pleased to present this repository containing a project on creation of a **gyro glove controlled vehicle with signal loss sound alert**. <br>
This project was completed as part of the Control Systems Technology course of my **Master's Degree in Computer Science and Engineering** at the **University of Catania**.

## ✨ Features  

- **Glove-Controlled Navigation**: Operates a 4-wheel vehicle using a glove equipped with a gyroscope sensor, allowing for intuitive gesture-based control.  
- **Real-Time Wireless Communication**: Transmits movement data from the glove to the vehicle using a 433MHz RF module, ensuring smooth and responsive operation.  
- **Forward and Backward Motion**: Moves the vehicle forward by tilting the glove downward and backward by tilting it upward, maintaining a constant speed.  
- **Steering Control**: Adjusts the direction of the vehicle by tilting the glove left or right, enabling fluid and natural turns.  
- **Signal Loss Detection**: Monitors the wireless connection and detects when the signal between the glove and the vehicle is lost.  
- **Audio Alert System**: Activates a buzzer alarm only when the signal is lost, playing a predefined melody to indicate disconnection.  
- **Embedded Systems Programming**: Utilizes Arduino microcontrollers to handle motion processing, wireless transmission, and vehicle control efficiently.  
- **Motor Control via H-Bridge**: Implements an H-Bridge motor driver module to manage the movement of the vehicle’s motors with fixed-speed operation.  
- **Compact and Efficient Design**: Integrates a gyroscope, RF transmitter and receiver, buzzer module, and DC motors, ensuring a reliable and portable system.  
- **Comprehensive Project Resources**: Includes fully documented Arduino scripts and detailed images to facilitate setup.  

## 🎥 Preview 

Watch a **playlist of video demonstrations** on YouTube showcasing the project’s key features and functionalities:

[![YouTube](https://img.shields.io/badge/Watch%20on-YouTube-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/playlist?list=PLH5TcNmVj9SKg2pTg-hA4ib_r6gVrMaNA)

## 🛠️ Tech Stack

- **Embedded System Development**:  
  - **Arduino IDE** for writing, compiling, and uploading the code to the microcontroller.  
  - **C/C++** for programming the embedded system logic.  
- **Hardware Components**:  
  - **Arduino microcontroller** for processing inputs and controlling the vehicle.  
  - **Gyroscope sensor** for detecting hand movements and tilt angles.  
  - **433MHz RF transmitter and receiver** for wireless communication between the glove and the vehicle.  
  - **H-Bridge motor driver** for managing motor direction and speed.  
  - **DC motors** for vehicle movement.  
  - **Buzzer module** for playing an alert sound when the signal is lost.  
- **Version Control**: Git for tracking changes and managing project versions.  
- **Repository Hosting**: GitHub for storing, sharing, and maintaining the project repository.  

## 🚀 Getting Started

### Prerequisites  

Ensure you have the following tools installed on your system before proceeding:  

- **Arduino IDE**: Required to read and understand code efficiently.  
- **Required Libraries**: Install the following libraries using the Arduino Library Manager: 
  - **MPU6050_tockn**: Required for gyroscope sensor integration.
  - **Wire**: Required for I2C communication with the gyroscope.  
  - **RH_ASK**: Required for handling RF transmission and reception.
  - **SPI**: Required for communication with the RF module.
- **USB Cable**: Required to upload code to the Arduino microcontrollers.
- **Power Source**: Required to supply power to the glove and vehicle modules.
- **Git**: Used to clone the repository. 

### Installation Steps  

1. **Clone the Repository**  

   To download the repository and navigate to its directory:

   ```sh
   git clone https://github.com/stefanocaramagno/Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert.git
   cd Gyro_Glove_Controlled_Vehicle_with_Signal_Loss_Sound_Alert
   ```

2. **Install Required Libraries**

    Open Arduino IDE and install the necessary libraries:

    - Go to Sketch → Include Library → Manage Libraries.
    - Search for MPU6050_tockn and click Install.
    - Search for RH_ASK and click Install.
    - Ensure Wire and SPI libraries are installed (they are usually pre-installed in Arduino IDE).

3. **Upload the Code to the Vehicle**

    - Open vehicle_script.ino in Arduino IDE.
    - Connect the Arduino board inside the vehicle to your PC via USB.
    - Select the correct board and port.
    - Click Upload to flash the code to the microcontroller.

4. **Hardware Setup & Wiring**

    - Ensure the gyroscope sensor is properly positioned in the glove.
    - Verify that the 433MHz RF transmitter is connected to the glove's Arduino.
    - Check that the 433MHz RF receiver is connected to the vehicle's Arduino.
    - Connect the H-Bridge motor driver to the vehicle's motors and Arduino board.
    - Ensure the buzzer module is correctly wired for audio alerts.

5. **Power the System & Test**

    - Power the glove's Arduino using a battery or USB connection.
    - Power the vehicle's Arduino and motor driver using an appropriate battery source.
    - Tilt the glove to test vehicle movement.
    - Move the glove out of range to trigger the signal loss alert via the buzzer.

##  🌐 Connect with Me

Feel free to explore my professional journey, check out my projects, or get in touch through the following platforms:

[![Email](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:stefano.caramagno@gmail.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-%2300A36C?style=for-the-badge&logo=buffer&logoColor=white)](https://stefanocaramagno.vercel.app)
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/stefanocaramagno)
[![Indeed](https://img.shields.io/badge/Indeed-%2300A4CC?style=for-the-badge&logo=indeed&logoColor=white)](https://profile.indeed.com/p/stefanoc-4cl1mmq)
[![GitHub](https://img.shields.io/badge/GitHub-%232F2F2F?style=for-the-badge&logo=github&logoColor=white)](https://github.com/stefanocaramagno)
[![YouTube](https://img.shields.io/badge/YouTube-D14836?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@stefanocaramagno)

## ⚖️ License

© **Stefano Caramagno**

**Personal and Educational Use Only**  
All content in this repository is provided for personal and educational purposes only. <br>
Unauthorized actions without explicit permission from the author are prohibited, including but not limited to:

- **Commercial Use**: Using any part of the content for commercial purposes.
- **Distribution**: Sharing or distributing the content to third parties.
- **Modification**: Altering, transforming, or building upon the content.
- **Resale**: Selling or licensing the content or any derivatives.

For permissions beyond the scope of this license, please contact the author.

**Disclaimer**  
The content is provided "*as is*" without warranty of any kind, express or implied. <br>
The author shall not be liable for any claims, damages, or other liabilities arising from its use.