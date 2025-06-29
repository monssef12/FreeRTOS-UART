FreeRTOS UART Echo Example
Overview
This project demonstrates the use of FreeRTOS tasks and queues to implement a UART echo application on an STM32 microcontroller. It highlights how to handle UART communication in a multitasking environment without relying on interrupts.

Features
FreeRTOS-based multitasking: Separate tasks for UART reception and transmission.

Queue-based communication: UART data is safely passed between tasks using FreeRTOS queues.

Blocking UART reception: Receives data character-by-character in a dedicated task.

Buffered UART transmission: Accumulates characters until an entire message (terminated by \r\n) is received and then sends the complete message back.

Simple, clean, and portable design for easy understanding and extension.

Project Structure
main.c — Initializes peripherals, creates FreeRTOS tasks, and starts the scheduler.

StartUartReceive task — Blocks on UART reception, pushing received bytes into a FreeRTOS queue.

StartUartSend task — Collects bytes from the queue, buffers them, and transmits complete messages upon detecting newline sequences.

FreeRTOS queue — Handles safe communication between receive and send tasks.

Usage
Connect the STM32 UART pins to a serial terminal (e.g., Tera Term) at 115200 baud.

Type messages in the terminal, ending each message with Enter (carriage return + newline).

The STM32 device will echo back the entire message once the line ending is received.

Notes
This example uses blocking UART reception to emphasize FreeRTOS task synchronization and queue communication rather than interrupt-driven UART.

Ensure that no UART interrupts are enabled to avoid conflicts with blocking reception.

The buffer size is fixed (128 bytes); messages longer than this will be truncated.

Requirements
STM32Cube HAL library

FreeRTOS kernel

STM32 development environment (e.g., STM32CubeIDE)

License
This project is provided as-is without warranty. You are free to use and modify it for educational and development purposes.

Happy coding with FreeRTOS and STM32!