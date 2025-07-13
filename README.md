# ISAP-1 Computer
The ISAP-1 Computer is the improved version of the SAP-1 computer made by me.

ISAP Computer stands for Improved Simple as Possible Computer.

By: Lincă Marius Gheorghe,

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

## ISAP-1 version 0.1
The initial version I want to be a redesign of the SAP-1 computer. For this purpose, we must go through the steps followed by the authors of the original project.

Version 0.1 will be an implementation of the SAP-1 computer that is as close to the original as possible. This will be the reference, the starting point for creating a better version.

The instruction set consists only of the NOP instruction.

### Block Diagram
The first stage of any project is drawing the Block Diagram, which allows you to visualize the overall picture of the designed system, where you can see the component blocks and the connections between them.

The analysis of the Block Diagram of the SAP-1 computer is the starting point for the creation of the ISAP-1 computer:

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Instruction Set Analysis
In this step, the original Instruction Set of the SAP-1 Computer is studied.

I will redraw the Timing Diagrams for each instruction individually.

I will also present the Truth Tables corresponding to each instruction.

All this information is necessary for understanding the operation of the SAP-1 computer but also for designing the Control Unit:

https://github.com/LincaMarius/ISAP-1_Instruction_Set

### Computer Simulation in Logisim
In this step, the ISAP-1 Computer is simulated using Logisim software, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.

In this way, design errors can be detected that can lead to wasted time later with debugging with a product that is partially functional or totally non-functional.

This is the process of creating the ISAP-1 computer at the simulation level using Logisim, presented step by step:

https://github.com/LincaMarius/ISAP-1_Logisim_Simulation

### Control Block Design using Combinational Logic
This step is necessary to complete the previous step.

I treated the Control Block design separately because it is more complicated and involves several distinct stages.

Here I designed the Control Block from scratch starting from the Boolean equations determined in step 2 when I studied the instruction set of the SAP-1 computer.

The goal was to design the Control Block using only logic gates (Combinational Logic) exactly as the authors of the SAP-1 computer did.

The goal was achieved, because in the end I obtained the same schematic as the one used in building the SAP-1 computer: \
https://github.com/LincaMarius/ISAP-1_Control_Unit

