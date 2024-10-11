# Robomaster A STM32 Controller

This repository contains the STM32 firmware designed for the **Robomaster A** board. The program facilitates seamless communication and control between the Robomaster A board and the TX2 module using the CAN bus and PWM outputs.

## Features

### 1. Motor and Servo Control
- **CAN Bus Communication (ID: 0x233):**
  - **Receiving Commands:** The firmware listens for motor and servo control commands from the TX2 module via the CAN bus.
  - **PWM Output Control:** Upon receiving the commands, it translates them into PWM signals to control the motors and servos.
  
- **Data Mapping:**
  - `send.Data[0]` and `send.Data[1]`: Represent **Steering Angle** data.
  - `send.Data[2]` and `send.Data[3]`: Represent **Speed** data.
  
- **PWM Channels Configuration:**
  - **TIM4 Channels 1 & 2 (`TIM_CHANNEL_1` & `TIM_CHANNEL_2`):**
    - **Function:** Receive and output `pwm_value1` to control the **Steering Angle**.
    - **Pin Mapping:** Correspond to PD12 (H) and PD13 (G) on the Robomaster A board.
  - **TIM4 Channels 3 & 4 (`TIM_CHANNEL_3` & `TIM_CHANNEL_4`):**
    - **Function:** Receive and output `pwm_value2` to control the **Speed**.
    - **Pin Mapping:** Correspond to PD14 (F) and PD15 (E) on the Robomaster A board.

### 2. Frequency Monitoring and Publishing
- **PI0(A) Interface:**
  - **Frequency Detection:** Monitors the high and low level transitions on the PI0(A) interface to determine frequency changes.
  
- **CAN Bus Communication (ID: 0x433):**
  - **Publishing Frequency Data:** Sends the detected frequency data to the TX2 module via the CAN bus.

## Hardware Requirements
- **Microcontroller:** STM32 series (compatible with Robomaster A board)
- **Development Board:** Robomaster A
- **Communication Modules:** CAN bus interface, TX2 module
- **Peripherals:** Motors, servos connected via PWM channels