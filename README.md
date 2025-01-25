# ISAP-1 Computer
The ISAP-1 computer is the improved version of the SAP-1 computer made by me.

ISAP Computer stands for Improved Simple as Possible Computer.

By: Lincă Marius Gheorghe.

Pitești, Argeș, Romania, Europe.

https://github.com/LincaMarius

## About the project, brief description

The goal of this project is to create a more efficient version of the SAP-1 (Simple As Possible) Computer.
    
Credits are given to Albert Paul Malvino and Jerald A. Brown for introducing this architecture in their book "Digital Computer Electronics" and Ben Eater for implementing his own version of the SAP Computer using IC's and breadboards.

References: 
- Ben Eater's 8 Bit computer videos. Building an 8-bit breadboard computer! https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU
- Digital Computer Electronics - Albert Paul Malvino (Page 141).

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video: \
 https://www.youtube.com/watch?v=KkTMICyp6xA. \ 
 She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## ISAP-1 Model A Version 1
The initial version I want to be a redesign of the SAP-1 computer. For this purpose, we must go through the steps followed by the authors of the original project.

Model A, I want to be an implementation of the SAP-1 computer that has the Control Unit made with logic gates.

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
In this step, the ISAP-1 Computer is simulated using Logisim software, testing functionality from a logical point of view before creating the electrical diagram or physical circuit.

In this way, design errors can be detected that can lead to wasted time later with debugging with a product that is partially functional or totally non-functional.

This is the process of creating the ISAP-1 computer at the simulation level using the Logisim program, presented step by step: \
https://github.com/LincaMarius/ISAP-1_Logisim_Simulation

### Step 4 – Control Block Design using Combinational Logic
This step is necessary to complete the previous step.

I treated the Control Block design separately because it is more complicated and involves several distinct stages.

Here I designed the Control Block from scratch starting from the Boolean equations determined in step 2 when I studied the instruction set of the SAP-1 computer.

The goal was to design the Control Block using only logic gates (Combinational Logic) exactly as the authors of the SAP-1 computer did.

The goal was achieved, because in the end I obtained the same schematic as the one used in building the SAP-1 computer. \
https://github.com/LincaMarius/ISAP-1_Control_Unit

### Step 5 – ISAP-1 Computer Test Programs
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation level by running programs designed for this purpose.

These programs are written in assembly code specific to the SAP-1 computer.

Like any other computer, the ISAP-1 only recognizes and interprets instructions as binary code.

Since there is no Assembler software that recognizes the syntax of the SAP-1 and ISAP-1 computer, the conversion from assembly language to binary code will be done manually.

All programs that can run on SAP-1 and ISAP-1 computers are here: \
https://github.com/LincaMarius/ISAP-1_Programs

### Step 6 – Electronic Schematic Design
In this step, the electronic components that will be used are chosen and the electronic diagram of the computer is designed as a complete assembly but also at the functional block level.

In this version I have restored the original schematic of the SAP-1 computer to preserve the original functionality.

I used the same electronic components and kept the chip numbering from the original schematic.

The original computer has a built-in power supply with a mains transformer and a linear regulator. 

The operating mode of the SAP-1 computer is to set the "Programming" mode and edit the RAM memory contents, then switch to "Run" mode when the program is executed and the result is displayed on the digital display.

So, on the display I will only have the result, and if the program is wrong I cannot verify its contents, and if one of the modules is not working correctly I cannot verify this except using test equipment.

The Electronic Diagram of the ISAP-1 Computer edited using the KiCAD program can be found here: \
https://github.com/LincaMarius/ISAP-1_Schematic

## ISAP-1 Model A Version 1.1
In the book on page 163 the authors present a method of improving the SAP-1 Computer by implementing the Variable Machine Cycle.

The schematic is shown in Figure 10-17 and consists of 5 inverters and a 12-input NAND gate that generates the #NOP signal when the Control Block output has the NOP instruction encoded in Hexadecimal as 3E3h and a two-input AND gate that resets the Ring Counter when the #NOP or #CLR signal is low. 

### Block Diagram optimization
The implementation of the Variable Machine Cycle is done inside the Control Block so the Block Diagram of the ISAP-1 Computer remains unchanged.

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Instruction Set Analysis
The instruction set does not change, but we need to update the timing diagrams and Boolean equations to incorporate the Variable Machine Cycle.

https://github.com/LincaMarius/ISAP-1_Instruction_Set?tab=readme-ov-file#isap-1-model-a-version-11

### Computer Simulation in Logisim
Since we are modifying the structure of the Control Block, we also need to modify the simulation of the ISAP-1 computer in the Logisim program.

https://github.com/LincaMarius/ISAP-1_Logisim_Simulation?tab=readme-ov-file#isap-1-model-a-version-11

### Control Block Design using Combinational Logic
This step is necessary to complete the previous step.

https://github.com/LincaMarius/ISAP-1_Control_Unit#isap-1-model-a-version-11

### ISAP-1 Computer Test Programs
All programs that run on the SAP-1 Model A Version 1 computer can also run without problems on the ISAP-1 Model A Version 1.1 computer.

All programs that can run on ISAP-1 Model A Version 1 and ISAP-1 Model A Version 1.1 computers are here: \
https://github.com/LincaMarius/ISAP-1_Programs

### Electronic Schematic Design
In this step, the electronic components that will be used are chosen and the electronic diagram of the computer is designed as a complete assembly but also at the functional block level.

The Schematic of the ISAP-1 Model A Computer Version 1.1 edited using the KiCAD program can be found here: \
https://github.com/LincaMarius/ISAP-1_Schematic#isap-1-model-a-version-11

## ISAP-1 Model B Version 1
Model B, I want to be an implementation of the SAP-1 Computer that has the Control Unit made using microprogramming and storing microinstructions in ROM memory.

I want Version 1 to be an implementation of the SAP-1 Computer that is as close to the original as possible. This will be the reference, the starting point for creating a better version.

### Step 1 – Block Diagram optimization
The Block Diagram remains unchanged for Model B of the SAP-1 and ISAP-1 Computers compared to Model A Version 1.0.

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Step 2 – Instruction Set Analysis
The Instruction Set remains unchanged for the Model B of the SAP-1 and ISAP-1 Computers compared to the Model A Version 1.0.

https://github.com/LincaMarius/ISAP-1_Instruction_Set

### Step 3 – Computer Simulation in Logisim
In this step, the ISAP-1 Model B Computer is simulated in Logisim software, where functionality is tested from a logical point of view before creating the electrical diagram or physical circuit.

The design and simulation of the ISAP-1 Model B Version 1.0 computer using Logisim software is presented here: \
https://github.com/LincaMarius/ISAP-1_Logisim_Simulation#isap-1-model-b-version-10

### Step 4 – Control Block Design using Programmed Logic
This step is necessary to complete the previous step.

Here I modified the Control Block diagram according to the instructions in the book starting with page 161 to page 163 in subchapter 10-8.

The goal was to design the Control Block used in the implementation of the Control Matrix using ROM memories instead of logic gates.

This was accomplished because in the end I obtained the scheme that uses only 10 chips compared to 18 chips in the previous implementation of the Model A. \
https://github.com/LincaMarius/ISAP-1_Control_Unit#isap-1-model-b-version-10

### Step 5 – ISAP-1 Computer Test Programs
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation level by running programs designed for this purpose.

The Model B Version 1.0 of the ISAP-1 Computer successfully ran all the programs here: \
https://github.com/LincaMarius/ISAP-1_Programs

### Step 6 – Electronic Schematic Design
In this step, the electronic components that will be used are chosen and the electronic diagram of the computer is designed as a complete assembly but also at the functional block level.

The Electronic Schematic Project of the ISAP-1 Computer Model B Version 1.0 edited using the KiCAD program can be found here: \
https://github.com/LincaMarius/ISAP-1_Schematic#isap-1-model-b-version-10

## ISAP-1 Model B Version 1.1
In the book on page 163 the authors present a method of improving the SAP-1 Computer by implementing the Variable Machine Cycle.

The schematic is shown in Figure 10-17 and consists of a 12-input NAND gate that generates the #NOP signal when the Control Block output has the NOP instruction encoded in Hexadecimal as 3E3h and a two-input AND gate that resets the Ring Counter when the #NOP or #CLR signal is low.

We can note that the SAP-1 Computer schematic is not modified to implement this functionality, only two logic gates are added.

### Block Diagram optimization
The implementation of the Variable Machine Cycle is done inside the Control Block so the Block Diagram of the ISAP-1 Computer remains unchanged.

https://github.com/LincaMarius/ISAP-1_Block_Diagram

### Instruction Set Analysis
The instruction set does not change, but we need to update the timing diagrams and Boolean equations to incorporate the Variable Machine Cycle.

Thus, we have the Revision 2 Instruction Set

https://github.com/LincaMarius/ISAP-1_Instruction_Set#isap-1-computer-instruction-set-revision-2

### Computer Simulation in Logisim
Since we are modifying the structure of the Control Block, we also need to modify the simulation of the ISAP-1 computer in the Logisim program.

https://github.com/LincaMarius/ISAP-1_Logisim_Simulation#isap-1-model-b-version-11

### Control Block Design using ROM memories
This step is necessary to complete the previous step.

https://github.com/LincaMarius/ISAP-1_Control_Unit#isap-1-model-b-version-11

### ISAP-1 Computer Test Programs
In this step, the functionality of the ISAP-1 computer as a whole is tested at the simulation level by running programs designed for this purpose.

All programs that can run on SAP-1 and ISAP-1 computers are here: \
https://github.com/LincaMarius/ISAP-1_Programs

### Step 6 – Electronic Schematic Design
In this step, the electronic components that will be used are chosen and the electronic diagram of the computer is designed as a complete assembly but also at the functional block level.

The Schematic of the ISAP-1 Model B computer Version 1.1 edited using the KiCAD program can be found here: \
https://github.com/LincaMarius/ISAP-1_Schematic


