# ISAP-1 Computer

The ISAP-1 computer is the improved version of the SAP-1 computer made by me.

This is the first stage of the design of the ISAP-1 computer and consists of the process of optimizing the functionality of the SAP-1 computer at the block diagram level.

By: Lincă Marius Gheorghe.

Pitești, Argeș, România, Europe.

https://github.com/LincaMarius


## About the project, brief description

The goal of this project is to create a more efficient version of the SAP (Simple As Possible) Computer.
    
Credits are given to Albert Paul Malvino and Jerald A. Brown for introducing this architecture in their book "Digital Computer Electronics" and Ben Eater for implementing his own version of the SAP Computer using IC's and breadboards.

References: 
- Ben Eater's 8 Bit computer videos. Building an 8-bit breadboard computer! https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU
- Digital Computer Electronics - Albert Paul Malvino (Page 141).

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video: https://www.youtube.com/watch?v=KkTMICyp6xA. She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## Design improvement by analyzing and modifying the block diagram of the SAP-1 computer

### Original block diagram

The original Block Diagram of the SAP-1 computer can be found in the book "Digital Computer Electronics" by Albert Paul Malvino and Jerald A. Brown, on page 141 and is labeled Figure 10-1.

In the following figure, I present a reproduction of the original block diagram of the SAP-1 computer.

![ Figure 1 ](/Pictures/Figure1.png)

I studied the original electronic schematic of the SAP-1 computer and recreated the block diagram to represent the actual functional blocks as closely as possible and I present it in the following figure.

![ Figure 2 ](/Pictures/Figure2.png)

The programming mode of the SAP-1 computer described by the authors is as follows:\
a.	Move the selector S2 to the PROG position,\
b.	The memory address to be modified is selected from switches S1,\
c.	Select from the S3 switches the date that you want to be written in the memory at the previously set address,\
d.	Press button S4 to write the new value to memory,\
e.	Repeat steps b, c and d until all necessary changes have been made, \
f.	Move selector S2 to the RUN position, to run the program.

In the diagram in figure 2 it can be seen that some of the control signals are active high and some are active low. This is due to the fact that the circuit diagram is optimized for the TTL integrated circuits used by the authors of the original design of the SAP-1 computer.

To simplify and ease the process of designing the Control Block I propose that in this phase of the design we use only active high control signals. Thus, the time charts will be easier to understand.

The block diagram using signals only active high control signals, can be seen in the following figure.

![ Figure 3 ](/Pictures/Figure3.png)

### Identification of computer components

As we learned at school, a computer can be represented by 3 distinct functional blocks: CPU, Memory and I/O. They are interconnected by 3 buses: the Data Bus, the Address Bus and the Control Bus.

This fact is also presented by the authors in the book in a simplified form on page 213 in figure 13-1.

A diagram representing a computing system consisting of functional blocks CPU, RAM, I/O and buses is presented in the following figure.

![ Figure 4 ](/Pictures/Figure4.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W bus".

So, I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. We get the following block diagram.

![ Figure 5 ](/Pictures/Figure5.png)

### Separation of the Central Processing Unit subsystem

I propose to separate the component blocks of the Central Processing Unit from the other blocks of the computer.

Thus from figure 5 we will remove the following blocks and their associated control signals:
- Address Select Switches,
- Program / Run Selector + Deposit,
- Date Select Switches,
- Clock and Reset,
- Address MUX,
- 16 x 8 RAM,
- Output Register
- Binary Display.

The resulting block diagram is shown in the following figure

![ Figure 6 ](/Pictures/Figure6.png)

Now I have renamed the Memory Address Register as the Address Register

In order to be able to highlight the three buses of the system, we must reverse the positions in the diagram of the Program Counter and the Address Register

The resulting block diagram is shown in the following figure

![ Figure 7 ](/Pictures/Figure7.png)

The CE signal was renamed DM – Data Memory Select \
The LM signal was renamed LAR - Load Address Register \
The LO signal has been renamed I/O \
I introduced the R/W signal to control RAM Read/Write.

### Improved design by adding possibility for Program Counter to be preset
From the block diagram it can be seen that the Program Counter cannot be loaded with a desired value.

The first, simplest improvement is to make the Program Counter loadable with any value present on the W bus if the new LP control signal is active.

![ Figure 8 ](/Pictures/Figure8.png)

The ability to load numeric values into the Program Counter allows us to extend the computer's instruction set by implementing the Unconditional Jump instruction.

### Improved system design by adding a Flags register
To run more advanced programs that need conditional jumps, we have to use flags that show us particulars of the result of the last arithmetic operation performed. These result characteristics are stored in the flags register.

These Flags can be tested individually or grouped, for this system I will use a selector for Flags, so only one condition is tested at a time.

The block diagram of the system that also has the flags register is shown in figure 9

![ Figure 9 ](/Pictures/Figure9.png)

I added the following control signals:
- PM – Program Memory – activates operations with Program Memory. In the case of the ISAP-1 computer we will have a ROM memory.
- INT – input from the I/O subsystem for activating the interrupt system
- SCF – Set Carry Flag
- CCF – Clear Carry Flag
- Flags Select – allows selection of the Flag of interest when executing a conditional jump instruction
- F – input to the Control Unit showing the status of the selected Flag

### Improved system design by loading the lower Nibble and upper Nibble of the Accumulator register separately
To run programs that allow immediate values to be loaded into the 8-bit Accumulator Register, since the Load Accumulator Immediate (LAI) instruction allows 4-bit values equivalent to a nibble, I decided to implement two separate instructions.

LIL instruction – Load immediate value into lower nibble and LIH instruction – Load immediate value into upper nibble.

The block diagram of the system that has the Accumulator register with separate charge signals for each nibble is shown in figure 10

![ Figure 10 ](/Pictures/Figure10.png)



## Summary
The final structure of the ISAP-1 computer is:

![ Figure 10 ](/Pictures/Figure10.png)

We can distinguish the three subsystems of the computer:
- The ISAP-1 CPU subsystem
- The Memory Subsystem
- Subsystem Inputs/Outputs

They are interconnected through the three mains:
- 4-bit address bus
- 8-bit data bus
- 5-bit command bus

Following is the optimization of the SAP-1 computer instruction set for the final block diagram that is present in this repository: \
https://github.com/LincaMarius/ISAP-1_Computer_Instruction_Set
