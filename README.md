# ISAP-1 Computer
The ISAP-1 Computer is the improved version of the SAP-1 computer made by me.

ISAP Computer stands for Improved Simple as Possible Computer.

By: Lincă Marius Gheorghe,

Pitești, Argeș, Romania, Europe.

https://github.com/LincaMarius

## About the project, brief description
The goal of this project is to create a more efficient version of the SAP-1 (Simple As Possible) computer, but with minimal changes so that the instruction format remains the same.
  
Credits are given to Albert Paul Malvino and Jerald A. Brown for introducing this architecture in their book "Digital Computer Electronics" and Ben Eater for implementing his own version of the SAP Computer using IC's and breadboards.

References: 
- Ben Eater's 8 Bit computer videos. Building an 8-bit breadboard computer! https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU
- Digital Computer Electronics - Albert Paul Malvino (Page 141).

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video:

 https://www.youtube.com/watch?v=KkTMICyp6xA.

 She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## ISAP-1 version 1.0
The initial version I want to be a redesign of the SAP-1 computer. For this purpose, we must go through the steps followed by the authors of the original project.

Version 1.0 will be an implementation of the SAP-1 computer that is as close to the original as possible. This will be the reference, the starting point for creating a better version.

### Step 1 – Block Diagram optimization
The first stage of any project is drawing the Block Diagram, which allows you to visualize the overall picture of the designed system, where you can see the component blocks and the connections between them.

The analysis of the Block Diagram of the SAP-1 computer is the starting point for the creation of the ISAP-1 computer:

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Step 2 – Instruction Set Analysis
In this step, the original Instruction Set of the SAP-1 Computer is studied.

I will redraw the Timing Diagrams for each instruction individually.

I will also present the Truth Tables corresponding to each instruction.

All this information is necessary for understanding the operation of the SAP-1 computer but also for designing the Control Unit.

https://github.com/LincaMarius/ISAP-1_Instruction_Set

### Step 3 – Computer Simulation in Logisim
In this step, the ISAP-1 Computer is simulated using Logisim software, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.

In this way, design errors can be detected that can lead to wasted time later with debugging with a product that is partially functional or totally non-functional.

This is the process of creating the ISAP-1 computer at the simulation level using Logisim, presented step by step:

https://github.com/LincaMarius/ISAP-1_Logisim_Simulation

### Step 4 – Control Block Design using Combinational Logic
This step is necessary to complete the previous step.

I treated the Control Block design separately because it is more complicated and involves several distinct stages.

Here I designed the Control Block from scratch starting from the Boolean equations determined in step 2 when I studied the instruction set of the SAP-1 computer.

The goal was to design the Control Block using only logic gates (Combinational Logic) exactly as the authors of the SAP-1 computer did.

The goal was achieved, because in the end I obtained the same schematic as the one used in building the SAP-1 computer.

https://github.com/LincaMarius/ISAP-1_Control_Unit

### Step 5 – ISAP-1 Computer Test Programs
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation level by running programs designed for this purpose.

These programs are written in assembly code specific to the SAP-1 computer.

Like any other computer, the ISAP-1 only recognizes and interprets instructions as binary code.

Since there is no Assembler software that recognizes the syntax of the SAP-1 and ISAP-1 computer, the conversion from assembly language to binary code will be done manually.

All programs that can run on SAP-1 and ISAP-1 computers are here:

https://github.com/LincaMarius/ISAP-1_Programs

### Step 6 – Schematic Design
In this step, the electronic components that will be used are chosen and the Schematic Diagram of the computer is designed as a complete assembly but also at the functional block level.

#### ISAP-1 TTL Version 1.0
In this version I have restored the original schematic of the SAP-1 computer to preserve the original functionality.

I used the same electronic components and kept the chip numbering from the original schematic.

The original computer has a built-in power supply with a mains transformer and a linear regulator. 

The operating mode of the SAP-1 computer is to set the "Programming" mode and edit the RAM memory contents, then switch to "Run" mode when the program is executed and the result is displayed on the binary display.

So, on the display I will only have the result, and if the program is wrong I cannot verify its contents, and if one of the modules is not working correctly I cannot verify this except using test equipment.

The Electronic Diagram of the ISAP-1 Computer edited using the KiCAD program can be found here:

https://github.com/LincaMarius/ISAP-1_Schematic

