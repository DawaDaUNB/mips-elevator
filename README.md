# mips-elevator

# **Implementation Details:**

# *Objective*: 
Create an elevator control system simulation using MIPS assembly language. This project aims to simulate the basic operations of an elevator, handling floor requests and managing elevator movements efficiently. 

This code is to be a generic system for 5 floor (or fewer, which can be achieved by ensuring the elevator is never given a button to move to a non-existant floor) elevators, with any function relating to hardware being stubbed with terminal input.

***Description***: 
- *Basic logic*: Implements a system that simulates an elevator capable of serving a fixed number of 5 floors. The program is able to take floor requests and move the elevator accordingly, displaying the current floor and direction of movement.
- *Request Queue*: Includes a request handling system that efficiently manages multiple floor requests, prioritizing them based on the current direction of the elevator and its position to minimize wait times.
- *Emergency Features*: Incorporates emergency functionalities, such as an emergency stop that halts the elevator until reset, and an alarm system that can be activated by the user.

# Interfaces:

The following registers are reserved for values provided by or the hardware.
- s0: Provides the current location of the elevator (which floor it is on)
- s1-t5: provides the current state of the call buttons on each floor, in which '00' (0) indicates no activation, '10' (2) indicates up, '01' (1) indicates down and '11' (3) indicates both.
- s6: provides the current state of the buttons activated within the elevator, '11111' (31) indicating all 5 activated.
- s7: whether the elevator is currently queued to move up or down (1 indicates up)

- t8: indicates whether the doors should be open (1 indicates open)
- t9: indicates if the elevator should currently in motion. (1 indicates yes)

When using syscalls in stub implementations, the t8 and t9 variables will need to be temporarily preserved on the stack.

# Technical Requirements:
- Use MIPS assembly language programming and test with the MARS simulator.
- Structure the program with clear, modular code sections for initialization, request handling, movement control, and user interface.
- Employ system calls for basic input/output operation
- MIPS assembly source code with comprehensive comments to explain the purpose and functionality of the code segments.
