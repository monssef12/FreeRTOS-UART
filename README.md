# FreeRTOS UART Echo Example on STM32F4

## Overview
This project demonstrates the use of FreeRTOS tasks and queues to implement a UART echo(receive what send) application on an STM32f4 microcontroller. It highlights how to handle UART communication in a multitasking environment and without relying on interrupts.

## Features
- FreeRTOS-based multitasking with separate tasks for UART reception and transmission  
- Queue-based communication allowing data passing between tasks  
- Buffered UART transmission accumulating characters until a complete message (terminated by \r\n) is received, then sending the entire message back  
- Simple, clean, and portable design for easy understanding and extension

## Project Structure
- **main.c**: Initializes peripherals, creates FreeRTOS tasks, and starts the scheduler  
- **StartUartReceive task**: Blocks on UART reception, pushing received bytes into a FreeRTOS queue  
- **StartUartSend task**: Collects bytes from the queue, buffers them, and transmits complete messages upon detecting newline sequences  
- **uartQueue queue**: Handles safe communication between receive and send tasks

## Usage
Connect the STM32 UART pins to a serial terminal (such as Tera Term) configured for 115200 baud.  
Type messages in the terminal, ending each message with Enter (carriage return + newline).  
The STM32 device will echo back the entire message once the line ending is received.

## Notes
- This example uses blocking UART reception to emphasize FreeRTOS task synchronization and queue communication rather than interrupt-driven UART.  
- Ensure that UART interrupts are disabled to avoid conflicts with blocking reception.  
- The message buffer size is fixed at 128 bytes; longer messages will be truncated.

## Requirements
- STM32Cube HAL library  
- FreeRTOS kernel  
- STM32 development environment (for example, STM32CubeIDE)

## License
This project is provided as-is without warranty. You are free to use and modify it for educational and development purposes.

Happy coding with FreeRTOS and STM32!
