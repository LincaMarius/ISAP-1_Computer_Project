# ISAP-1 Computer version 0.1
The initial version I want to be a redesign of the SAP-1 computer. For this purpose, we must go through the steps followed by the authors of the original project.

Version 0.1 will be an implementation of the SAP-1 computer that is as close to the original as possible, capable of executing only the “Fetch” portion of an instruction. This will be the reference, the starting point for creating a better version.

## Instruction Set Analysis
In this step, the original Instruction Set of the SAP-1 Computer is studied.

I will redraw the Timing Diagrams for each instruction individually.

I will also present the Truth Tables corresponding to each instruction.

https://github.com/LincaMarius/ISAP-1_Instruction_Set

## Block Diagram
The first stage of any project is drawing the Block Diagram, which allows you to visualize the overall picture of the designed system, where you can see the component blocks and the connections between them.

The analysis of the Block Diagram of the SAP-1 computer is the starting point for the creation of the ISAP-1 computer:
https://github.com/LincaMarius/ISAP-1_Block_Diagram

## Control Block Design
This step is necessary to complete the next step.

I treated the Control Block design separately because it is more complicated and involves several distinct stages.

https://github.com/LincaMarius/ISAP-1_Control_Unit

## ISAP-1 Computer Simulation in Logisim
In this step, the ISAP-1 Computer is simulated using Logisim software, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.

In this way, design errors can be detected that can lead to wasted time later with debugging with a product that is partially functional or totally non-functional.

This is the process of creating the ISAP-1 computer at the simulation level using Logisim, presented step by step: \
https://github.com/LincaMarius/ISAP-1_Logisim_Simulation

## Test Programs for the ISAP-1 Computer
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation or prototype level by running programs designed for this purpose.

These programs are written in assembly code specific to the SAP-1 and ISAP-1 computers, respectively.

Like any other computer, the ISAP-1 only recognizes and interprets instructions as binary code.

Since there is no Assembler software that recognizes the syntax of the SAP-1 and ISAP-1 computer, the conversion from assembly language to binary code will be done manually.

All programs that can run on SAP-1 and ISAP-1 computers are here: \
https://github.com/LincaMarius/ISAP-1_Programs

