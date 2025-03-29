# mips-elevator

# **Implementation Details:**

# *Objective*: 
Create an elevator control system simulation using MIPS assembly language. This project aims to simulate the basic operations of an elevator, handling floor requests and managing elevator movements efficiently. 

This code is to be a generic system for 5 floor elevators, with any function relating to hardware being stubbed with terminal input via syscall 5. This will be simulated in a loop, with the assumption being that the elevator changes floor or door state once per loop in the main function.

***Description***: 
- *Basic logic*: Implements a system that simulates an elevator capable of serving a fixed number of 5 floors. The program is able to take floor requests and move the elevator accordingly, displaying the current floor and direction of movement.
- *Request Queue*: Includes a request handling system that efficiently manages multiple floor requests, prioritizing them based on the current direction of the elevator and its position to minimize wait times. This queue will be dynamically processed without memory allocation via a LOOK algorithm, taking on the closest task in the current direction and switching direction when no tasks remain ahead.
- *Emergency Features*: Incorporates emergency functionalities, such as an emergency stop that halts the elevator until reset, and an alarm system that can be activated by the user. When the emergency button is pressed, the elevator will print a warning with relevant info to the terminal and fully exit, requiring the system to be fully reinitialized before normal operation can resume.
- *Edge Cases*: when no requests exist, no movement shall be done.

# Interfaces:

The following registers are reserved for values provided by or the hardware.
- s0: Provides the current location of the elevator (which floor it is on) or, if between floors, the last floor at which it was seen.
- s1-s5: provides the current state of the call buttons on each floor, in which '00' (0) indicates no activation, '10' (2) indicates up, '01' (1) indicates down and '11' (3) indicates both.
- s6: provides the current state of the buttons activated within the elevator, '11111' (31) indicating all 5 activated. Bit 6 (100000) represents the emergency stop button.
- s7: whether the elevator is currently queued to move up or down (1 indicates up)

- t8: indicates whether the doors should be open (1 indicates open)
- t9: indicates if the elevator should currently in motion. (1 indicates yes)

When using syscalls in stub implementations, the t8 and t9 variables will need to be temporarily preserved on the stack.
The full system will be implemented in a main function looping between the 'checkFloor', 'getButtons', 'chooseDirection', and exactly one of 'moveDoors' *or* 'moveElevator'

# Technical Requirements:
- Use MIPS assembly language programming and test with the MARS simulator.
- Structure the program with clear, modular code sections for initialization, request handling, movement control, and user interface.
- Employ system calls for basic input/output operation
- MIPS assembly source code with comprehensive comments to explain the purpose and functionality of the code segments.
