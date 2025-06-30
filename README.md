# FreeRTOS UART Echo Example on STM32F4

## Overview
This project show how to use FreeRTOS tasks and queues to do a UART echo (send back what you received) on STM32F4 microcontroller. It’s good to see how UART can work in multitasking way without using interrupts.

## Prerequisites
To get this project, you better know some stuffs like:  
- Basic UART communication (baud rate, start/stop bits, framing and so on)  
- Hands-on with STM32 and STM32Cube HAL library  
- Some idea about FreeRTOS tasks, queues and multitasking  
- How to use serial terminal programs like Tera Term or PuTTY

## Features
- Using FreeRTOS multitasking: separate tasks for receiving and sending UART data  
- Communication between tasks using FreeRTOS queues  
- Buffering UART data until full message (ends with `\r\n`) then send it all back at once  
- Simple design easy to understand and change

## Project Structure
- **main.c**: Setup hardware, create tasks and start FreeRTOS scheduler  
- **StartUartReceive task**: Waits for UART data and puts received bytes in queue  
- **StartUartSend task**: Reads bytes from queue, stores them and sends full messages when newline detected  
- **uartQueue queue**: Used for safe communication between tasks

## Usage
Connect STM32 UART pins to serial terminal like **Tera Term** or **PuTTY**, and set:  
- Baud rate: 115200  
- Data bits: 8  
- Parity: None  
- Stop bits: 1  
- Flow control: None  

Type your message and press Enter (which sends carriage return + newline).  
STM32 will echo the whole message back after you press Enter.

## Notes
- This example use blocking UART receive to show how FreeRTOS tasks and queues works, instead of using interrupts.  
- Make sure UART interrupts are off, otherwise may conflict with blocking receive.  
- Buffer size is 128 bytes, longer message will cut off.

## Requirements
- STM32Cube HAL library  
- FreeRTOS kernel  
- STM32 IDE like STM32CubeIDE or similar

## License
This project is given as-is, no warranty. Feel free to use and modify for learning or your own projects.

Happy coding with FreeRTOS and STM32!
