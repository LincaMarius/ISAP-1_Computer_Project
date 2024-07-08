# SAP 1 Computer

The improved version of the SAP-1 computer.

This is the SAP-1 computer functionality optimization process at the block diagram level that I went through.

By: Lincă Marius Gheorghe.

Pitești, Argeș, România, Europe.

https://github.com/LincaMarius/ISAP-Computer


## About the project, brief description

The goal of this project is to create a more efficient version of the SAP (Simple As Possible) Computer.
    
Credits are given to Albert Paul Malvino and Jerald A. Brown for introducing this architecture in their book "Digital Computer Electronics" and Ben Eater for implementing his own version of the SAP Computer using IC's and breadboards.

References: 
- Ben Eater's 8 Bit computer videos. Building an 8-bit breadboard computer! https://www.youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU
- Digital Computer Electronics - Albert Paul Malvino (Page 141).

An interesting fact is that I discovered a girl who made the SAP-1 calculator using breadboards in October 2011, and Ben Eater in February 2015, so 4 years earlier! This is that video: https://www.youtube.com/watch?v=KkTMICyp6xA. She built the SAP-1 computer using breadboards for a school project. It's a pity that the video presented is not of better quality.

## Design improvement by analyzing and modifying the block diagram of the SAP-1 computer

The original Block Diagram of the SAP-1 computer can be found in the book "Digital Computer Electronics" by Albert Paul Malvino and Jerald A. Brown, on page 141 and is labeled Figure 10-1.

In the following figure, I present to you a reproduction of the block diagram of the SAP-1 computer.

![ Figure 1 ](/Pictures/Figure1.png)

I studied the original electronic schematic of the SAP-1 computer and recreated the block diagram to represent the actual functional blocks as closely as possible and I present it in the following figure.

![ Figure 2 ](/Pictures/Figure2.png)

The programming mode of the SAP-1 computer described by the authors is as follows:
a.	Move the selector S2 to the PROG position,
b.	The memory address to be modified is selected from switches S1,
c.	Select from the S3 switches the date that you want to be written in the memory at the previously set address,
d.	Press button S4 to write the new value to memory,
e.	Repeat steps b, c and d until all desired changes have been made,
f.	Move selector S2 to the RUN position, to run the program.

## Improved design by adding possibility for Program Counter to be preset

From the block diagram it can be seen that the Program Counter cannot be loaded with a desired value, thus we do not have the possibility to make jumps in the execution of the running programs.

So the first, simplest modification is to make the Program Counter able to be loaded with any value present on the W bus, if the new LP control signal is active. As can be seen in the following figure represented in green.

![ Figure 3 ](/Pictures/Figure3.png)

The ability to load numeric values into the Program Counter allows us to extend the computer's instruction set by implementing the unconditional jump instruction.

## Improving the design by adding a keyboard for entering input data

From Figure 3 it can be seen that there is no possibility for the user to interact with the computer while the program is running.

There is the S3 switch set but it can only be used in programming mode to change the RAM contents.

Thus, I removed the S3 switch set and introduced the Binary Input Keyboard block which also consists of 8 switches with the role of entering any 8-bit binary value.

When the command signal EK is active the binary value entered by the operator is presented on the W bus. Thus, it can be loaded into RAM during programming or into Accumulator during normal program runs.
The new elements introduced are represented in figure 4 in green.

![ Figure 4 ](/Pictures/Figure4.png)

Switch group S1 can now be used to select the address where the desired value is to be saved.

The Binary Input Keyboard block connects to the data bus through a buffer and is controlled by the Ek signal, so we can implement a new instruction called INPUT.

## Improved system design by eliminating manual address entries during programming

When we want to enter a new program, we will start programming with address 0 and increment this address by one to enter the next instruction, until all instructions have been entered. Even when checking a program we go through it line by line.

But we already have the Program Counter block that can do this incrementing automatically, so I propose removing the S1 switch group and using the Program Counter to automatically increment the address while programming the computer.

Thus, according to the block diagram, the contents of the Program Counter must be presented on the W bus from where it is loaded into the Memory Address Register. But at the same time the data we want to save from the keyboard must be present on the bus to be taken over by the RAM memory.

Now we have a problem because a collision occurs on the W bus. This situation is shown in figure 5, where the collision areas are shown in red.

![ Figure 5 ](/Pictures/Figure5.png)

To solve these problems, I propose the following solution:
- The position of the Memory Address Register and Address MUX blocks is reversed in the block diagram,
- The second input of the Address MUX block which was originally connected to the switch block S1 is connected to the output of the Program Counter block.

The Address MUX block is controlled by the /PGM signal and presents the connected inputs at the output:
- to bus W in RUN mode and
- at Program Counter in PROGRAMMING mode.

The new block diagram is shown in figure 6.

![ Figure 6 ](/Pictures/Figure6.png)

## Improved system design by adding a flags register

To run more advanced programs that need conditional jumps, we have to use flags that show us particulars of the result of the last arithmetic operation performed. These result characteristics are stored in the flags register.

These flags can be tested individually or grouped, for this system I will use a selector for flags, so only one condition is tested at a time.

The block diagram of the system that also has the flags register is shown in figure 7

![ Figure 7 ](/Pictures/Figure7.png)

## Improved system design by adding an interrupt entry

We have the Binary Input Keyboard block, and to make this keyboard interactive while running programs, the computer needs to see a confirmation signal from the operator, the equivalent of the Enter key on a normal computer.

I introduced the signal marked INT which means interrupt, in order to ensure the response for the computer from the operator after he has entered the data correctly.

The new block diagram is presented in figure 8.

![ Figure 8 ](/Pictures/Figure8.png)

## Identification of computer components

As we learned at school, a computer can be represented by 3 distinct functional blocks: CPU, Memory and I/O. They are interconnected by 3 buses: the Data Bus, the Address Bus and the Control Bus.

This fact is also presented by the authors in the book in a simplified form on page 213 in figure 13-1.

A diagram representing a computing system consisting of functional blocks CPU, RAM, I/O and buses is presented in the following figure.

![ Figure 9 ](/Pictures/Figure9.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W bus".

So, I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. We get the following block diagram.

![ Figure 10 ](/Pictures/Figure10.png)

Now I will do a re-layout of all the functional blocks so that we separate the CPU side from the memory and I/O. Thus, we obtained the following block diagram.

![ Figure 11 ](/Pictures/Figure11.png)

## Improving the system design by expanding the number of inputs-outputs

From figure 11 we can see that the system can only access two input/output devices. To improve I/O capabilities make the address bus accessible for I/O as well.

The new block diagram can be seen in figure 12.

By using an address decoder we can access a maximum of 16 inputs and 16 outputs.

![ Figure 12 ](/Pictures/Figure12.png)

## Improved system design by expanding accessed memory

The address bus is 4 bits so the maximum number of accessible memory locations will be: 2^4 = 16 locations. 

For very simple programs it may be enough. But is it possible to access more memory?

The simplest solution to this problem that I can think of, without changing the current structure very much, is to add a 16-byte ROM (or RAM that will be treated as Read-Only by the system) and add an additional control.

This memory becomes program memory, the old one will be data memory. The selection between the two types of memory is done with a control signal on which we write /PM from program memory, as we can see in figure 13.

![ Figure 13 ](/Pictures/Figure13.png)

## Improved system design by using a memory bank system

The previous solution doubles the accessed memory, resulting in 16 bytes of program memory and 16 bytes of data memory.

But I want to be able to access a lot more memory. The solution I thought of is to use a memory bank system.

A first variant is to use an 8-bit register to store the value of the accessed memory bank. Thus, we have 2^8 = 256 values for the bank. So, the maximum memory capacity that can be accessed is 16 x 256 = 4096 bytes.

In total 8k bytes of memory can be accessed. We can thus have a maximum of 256 programs of 16 bytes each.

The applied solution is presented in figure 14.

![ Figure 14 ](/Pictures/Figure14.png)

Each register that stores the value for the bank is attached to the system as an input-output port. We can read the information from the register but we can also write a new value to that register.

Since there are already many people who have built the version proposed by Ben Eater, or even bought the kit sold by him, they are in the situation of having only 16 bytes of memory in their computer.

Changing to the 4k byte system almost means rebuilding the computer. So I will use a variant of the memory system that only uses 16 bytes of RAM and the changes to the computer are minimal.

This simpler and easier to implement variant is the one where we use the bank register only for the ROM memory.

Loading this register can be done manually directly from the numeric keypad. Thus, I can manually select any of a maximum of 256 programs of 16 bytes each.

A more complicated variant involves loading this register by accessing it as an input-output port from the program. This solution is shown in figure 15.

![ Figure 15 ](/Pictures/Figure15.png)

This is the version that I will use to implement the memory system.

## Improved system design by removing address multiplexer

If we remove from the block diagram the memory and the input-output system, only part of the CPU remains, as can be seen in figure 16.

![ Figure 16 ](/Pictures/Figure16.png)

Since the program is no longer entered manually, but resides in ROM, it follows that the Address MUX block is no longer needed, so it must be removed. This results in the final system diagram of the CPU in the SAP-1 computer shown in figure 17.

![ Figure 17 ](/Pictures/Figure17.png)

## Summary

The final block diagram of the CPU part of the system is:

![ Figure 17 ](/Pictures/Figure17.png)

The final block diagram of the Computer Memory system is:

![ Figure 15 ](/Pictures/Figure15.png)

Optimization of the SAP-1 computer instruction set for the final block diagram follows.
