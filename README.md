# ISAP-1 Computer
The ISAP-1 computer is the improved version of the SAP-1 computer made by me.

ISAP Computer stands for Improved Simple as Possible Computer.

By: Lincă Marius Gheorghe.

Pitești, Argeș, România, Europe.

https://github.com/LincaMarius

## About the project, brief description

The goal of this project is to create a more efficient version of the SAP (Simple As Possible) Computer.
    
Credits are given to Albert Paul Malvino and Jerald A. Brown for introducing this architecture in their book "Digital Computer Electronics" and Ben Eater for implementing his own version of the SAP Computer using IC's and breadboards.

References: 
- Ben Eater's 8 Bit computer videos. Building an 8-bit breadboard computer! https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU
- Digital Computer Electronics - Albert Paul Malvino (Page 141).

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video: \
 https://www.youtube.com/watch?v=KkTMICyp6xA. \ 
 She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## ISAP-1 revision A version 1
The initial version I want to be a redesign of the SAP-1 computer. For this purpose, we must go through the steps followed by the authors of the original project.

Revision A, I want to be an implementation of the SAP-1 computer that has the Control Unit made with logic gates.

I want version 1 to be an implementation of the SAP-1 Computer that is as close to the original as possible. This will be the reference, the starting point for creating a better version.

### Step 1 – Block Diagram optimization
The first stage of any project is the realization of the block diagram through which the overall picture of the designed system can be viewed, where the component blocks and the links between them can be seen.

I will do an analysis of the original Block Diagram of the SAP-1 computer.

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Step 2 – Instruction Set Analysis
In this step, the original Instruction Set of the SAP-1 Computer is studied.

I will redraw the Timing Diagrams for each instruction individually.

I will also present the Truth Tables corresponding to each instruction.

All this information is necessary for understanding the operation of the SAP-1 computer but also for designing the Control Block.

https://github.com/LincaMarius/ISAP-1_Instruction_Set

### Step 3 – Computer Simulation in Logisim
In this step, the ISAP-1 Computer is simulated in the Logisim program, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.

In this way, design errors can be detected that can lead to wasted time later with debugging with a product that is partially functional or totally non-functional.

This is the process of creating the ISAP-1 computer at the simulation level using the Logisim program, presented step by step: \
https://github.com/LincaMarius/ISAP-1_Logisim_Simulation

### Step 4 – Control Block Design using Combinational Logic
This step is necessary to complete the previous step.

We treated the design of the Control Block separately because it is more complicated and involves several distinct stages.

Here we designed the Control Block from scratch starting from the Boolean formulas determined in step 2 when we studied the instruction set of the SAP-1 computer.

The goal was to design the Control Block using only logic gates (Combinational Logic) exactly as the authors of the SAP-1 computer did.

This was achieved because in the end we obtained the same scheme as the one used in the creation of the SAP-1 Computer: \
https://github.com/LincaMarius/ISAP-1_Control_Unit

### Step 5 – ISAP-1 Computer Test Programs
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation level by running programs designed for this purpose.

These programs are written in assembly code specific to the SAP-1 computer.

Like any other computer, the ISAP-1 only recognizes and interprets instructions as binary code.

Since there is no assembler program that recognizes the syntax of the SAP-1 and ISAP-1 computer, the conversion from assembly language to binary code will be done manually.

All programs that can run on SAP-1 and ISAP-1 computers are here: \
https://github.com/LincaMarius/ISAP-1_Programs

### Step 6 – Electronic Schematic Design
In this step, the electronic components that will be used are chosen and the electronic diagram of the computer is designed as a complete assembly but also at the functional block level.

In this version we have restored the original schematic of the SAP-1 computer to preserve the original functionality.

We used the same electronic components and kept the chip numbering from the original schematic.

The original computer has a built-in power supply with a mains transformer and a linear regulator. 

The ISAP-1 computer can be powered using an external 5 Volt DC power source with a Barrel Jack or a USB type A connector.

The operating mode of the SAP-1 computer is to set the Programming mode and edit RAM memory contents, then switch to Run mode when the program is executed and the result is displayed on the digital display.
So on the display I will only have the result, and if the program is wrong I cannot verify its contents, and if one of the modules is not working correctly I cannot verify this except using test equipment.

The Electronic Diagram of the ISAP-1 Computer edited using the KiCAD program can be found here: \
https://github.com/LincaMarius/ISAP-1_Schematic

## ISAP-1 revision B version 1
Revision B, I want to be an implementation of the SAP-1 computer that has the Control Unit made using microprogramming and storing microinstructions in ROM memory.

I want version 1 to be an implementation of the SAP-1 Computer that is as close to the original as possible. This will be the reference, the starting point for creating a better version.

The Block Diagram remains unchanged for Revision B of the SAP-1 and ISAP-1 computers compared to Revision A.

The Instruction Set remains unchanged for Revision B of the SAP-1 and ISAP-1 computers compared to Revision A.

### Step 3 – Computer Simulation in Logisim
In this step, the ISAP-1 Computer revision B is simulated in the Logisim program, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.


