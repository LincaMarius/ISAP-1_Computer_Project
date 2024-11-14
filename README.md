# ISAP-1 Computer

The ISAP-1 computer is the improved version of the SAP-1 computer made by me.

ISAP Computer stands for Improved Simple as Possible Computer

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

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video: \
 https://www.youtube.com/watch?v=KkTMICyp6xA. \ 
 She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## Design improvement by analyzing and modifying the block diagram of the SAP-1 computer

### Original block diagram

The original Block Diagram of the SAP-1 computer can be found in the book "Digital Computer Electronics" by Albert Paul Malvino and Jerald A. Brown, on page 141 and is labeled Figure 10-1.

In the following figure, I present a reproduction of the original block diagram of the SAP-1 computer.

![ Figure 1 ](/Pictures/Figure1.png)

### More detailed block diagram

I studied the original schematic of the SAP-1 computer and recreated the block diagram to represent the actual functional blocks as closely as possible and I present it in the following figure.

![ Figure 2 ](/Pictures/Figure2.png)

The programming mode of the SAP-1 computer described by the authors is as follows:\
a.	Move selector S2 to the PROG position, to enter Programming mode, \
b.	The memory address to be modified is selected with switches S1, \
c.	Select with the S3 switches the Data that you want to be written to the memory at the previously set address, \
d.	Press button S4 to write the new value to memory,\
e.	Repeat steps b, c and d until all necessary changes have been made, \
f.	Move selector S2 to the RUN position, to run the program.

### Block diagram using only active high control signals

In the diagram in figure 2 it can be seen that some of the control signals are active high and some are active low. This is due to the fact that the circuit diagram is optimized for the TTL integrated circuits used by the authors of the original design of the SAP-1 computer.

To simplify and ease the process of designing the Control Block I propose that in this phase of the design we use only active high control signals. Thus, the time charts will be easier to understand.

The block diagram using signals only active high control signals, can be seen in the following figure.

![ Figure 3 ](/Pictures/Figure3.png)

## Identifying and separating computer components

As we learned in school, a computer can be represented by 3 distinct functional blocks:
- CPU,
- Memory
- I/O.

They are interconnected through 3 buses that form the system bus:
- data bus,
- address bus
- the control bus.

This fact is also presented by the authors in the book in a simplified form on page 213 in figure 13-1.

A diagram representing a computing system consisting of functional blocks CPU, RAM, I/O and buses is presented in the following figure.

![ Figure 4 ](/Pictures/Figure4.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W bus".

So, I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. We get the following block diagram.

![ Figure 5 ](/Pictures/Figure5.png)

## Separation of the Central Processing Unit

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

The CE signal was renamed DM = Data Memory Select \
The LM signal was renamed LAR = Load Address Register \
The LO signal has been renamed I/O \
I introduced the R/W signal to control the Read/Write operation.

## Improved design by adding possibility for Program Counter to be preset
From the block diagram it can be seen that the Program Counter cannot be loaded with a desired value.

The first, simplest improvement is to make the Program Counter loadable with any value present on the W Bus if the new LP control signal is active.

![ Figure 8 ](/Pictures/Figure8.png)

The ability to load numeric values ​​into the Program Counter allows us to extend the computer's instruction set by implementing conditional jump and unconditional jump instructions.

## Improved system design by adding Flags
To run more advanced programs that need conditional jumps, we have to use Flags that show us particulars of the result of the last arithmetic operation performed. 
These result characteristics can be determined by evaluating the values ​​of the Flags.

These Flags can be tested individually or grouped, for this system I will use a selector for Flags, so only one condition is tested at a time.

The block diagram of the system that also has the flags register is shown in figure 9

![ Figure 9 ](/Pictures/Figure9.png)

I added the following control signals:
- PM – Program Memory – activates operations with Program Memory. In the case of the ISAP-1 computer we will have a ROM memory.
- INT – input from the I/O subsystem for activating the interrupt system

## Improved system design by loading the lower Nibble and upper Nibble of the Accumulator register separately
To run programs that allow immediate values to be loaded into the 8-bit Accumulator Register, since the Load Accumulator Immediate (LAI) instruction allows 4-bit values equivalent to a nibble, I decided to implement two separate instructions.

LIL instruction – Load immediate value into lower nibble and \ 
LIH instruction – Load immediate value into upper nibble.

The block diagram of the system that has the Accumulator register with separate charge signals for each nibble is shown in figure 10

![ Figure 10 ](/Pictures/Figure10.png)

The control signal LA is replaced by two new control signals:
- LAL – Lower Accumulator Nibble Register Load
- LAH – Upper Accumulator Nibble Register Load.

## Extending the Instruction Set
The original format of the SAP-1 computer instructions is:

| 4 bits instruction code   | 4 bits operand (memory address)          |
|---------------------------|------------------------------------------|

This means that a maximum of 2 ^ 4 = 16 memory locations can be accessed.

Since there are instructions that take parameters and instructions that do not require parameters, I will group the instructions without parameters into a separate set of instructions.

This instruction set will have a prefix. I chose the value 1111 binary, 0xF in hexadecimal.

| Extended instruction prefix 4 bits (0xF) | Extended instruction 4 bits (0xF) |
|------------------------------------------|-----------------------------------|

Thus, 15 instructions with parameters will remain and we will be able to implement 16 instructions without parameters.

We have an Instruction Set consisting of 31 instructions: 15 instructions with parameter and 16 instructions without parameter.

To modify the control signals optimally if we have to execute an extended instruction, the Control Block must receive all 8 bits stored in the Instruction Register. This causes the block diagram of the ISAP-1 computer to change as follows:

![ Figure 11 ](/Pictures/Figure11.png)

## Improved system design by adding a Constants Generator
Some instructions implicitly need a constant numeric value in their execution.

One such instruction is the INC instruction which increments a variable by one. Another statement is the SET statement which assigns the value one to a variable. Both instructions need the constant one.

To implement such instructions in the ISAP-1 computer, I introduced a Constant Generator in the block diagram.

It generates the value zero if no control signal is active.

Activating the EC1 signal has the effect of generating the value one.

On activation of the SC2 signal and generates the value -1.

Activation of the EC control signal puts the generated value on the Bus.

The block diagram of the system that has the Constant Generator block implemented is shown in figure 12.

![ Figure 12 ](/Pictures/Figure12.png)

## Improved system design by adding Stack
I decided to add stack operations to this calculator. Thus, I can implement calling subroutines as a first benefit. The stack also provides the ability to store data temporarily.

We will use a 4-bit register for the stack since the address is 4-bit. This register must be able to be incremented as well as decremented.

For this purpose we can use a counter. It must be able to be incremented but also decremented.

New instructions such as: PUSH, POP, CALL, RET, JMP FAR can now be implemented.

![ Figure 13 ](/Pictures/Figure13.png)

Since the available RAM is only 16 bytes we decided Stiva to use a separate RAM, so it doesn't reduce the space available for program variables.

Since the Stack doesn't use the computer's RAM, but has its own RAM, the Stack's growth direction doesn't matter.

## Improving Arithmetic and Logical capabilities
The basic structure of the SAP-1 calculator can only perform Addition and Subtraction operations.

To expand the operations that can be performed with this computer, a Logical Unit is added to allow the realization of shifting operations or logical operations at the bit level.

For this purpose, the new Logical and Arithmetic Unit requires several control signals. We have replaced the old control signal denoted SU with a group of control signals called FUNC.

Depending on the number of functions implemented, the number of control signals can be between 2 and 5, so between 4 and 32 functions can be executed.

For the ISAP-1 computer, I chose 3 control lines for the Logical and Arithmetic Unit command, involving the execution of a maximum of 8 functions.

The block diagram for the ISAP-1 computer using an ALU unit is shown in figure 14.

![ Figure 14 ](/Pictures/Figure14.png)

## Improvement of SAP-1 computer architecture
The architecture of the ISAP-1 computer up to this point is as follows:

![ Figure 15 ](/Pictures/Figure15.png)

We can distinguish the three subsystems of the computer:
- The ISAP-1 CPU
- The Memory Subsystem
- Inputs/Outputs Subsystem 

They are interconnected through the three buses:
- 4-bit address bus
- 8-bit data bus
- 6-bit commands bus

The available address space for the ISAP-1 computer in this structure is:
- 16 bytes of Program Memory
- 16 bytes of Data Memory
- 16 bytes Stack
- 16 Input-Output Devices

The obvious limitation is given by the size of the programs that can be run of only 16 bytes.

For this purpose, I propose the implementation of a Program Memory Banking system. This is done by using an external register that will be addressed as an Input-Output device. This register will be 8 bits.

So, the addressable Program Memory capacity will increase from 16 bytes to:
2^8 * 16 bytes = 256 * 16 bytes = 4096 bytes

The described Program Memory Banking model is shown in figure 15.

![ Figure 16 ](/Pictures/Figure16.png)

## Binary Keyboard
For any digital system we need a way to interact with it. This is the function of the Input-Output subsystem.

The simplest input system that can be realized is a binary keyboard that allows the transmission of a binary code set by means of 8 switches on the data bus of the ISAP-1 computer.

The connection of this Keyboard to the system buses is shown in figure 16.

![ Figure 16 ](/Pictures/Figure16.png)

## Binary Display
The simplest output device that can be connected to this computer is a Binary Display. This device is also used in the original construction of the SAP-1 computer, where it is integrated directly into the structure of this computer.

My modified version that allows connection to the ISAP-1 computer buses is shown in figure 17.

![ Figure 17 ](/Pictures/Figure17.png)

Following is the optimization of the SAP-1 computer instruction set for the final block diagram that is present in this repository: \
https://github.com/LincaMarius/ISAP-1_Computer_Instruction_Set
