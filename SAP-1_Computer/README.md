# SAP-1 Computer
The SAP-1 computer is introduced as a teaching project by Albert Paul Malvino and Jerald A. Brown in their book “Digital Computer Electronics”.

The description of its architecture and operation is presented in the book starting on Page 140 and the diagram starting on page 154. The Parts List is presented on page 501.

In this part of the project, I want to do an analysis of the SAP-1 computer.

## Block Diagram Analysis
The first stage of any project is drawing the Block Diagram, which allows you to visualize the overall picture of the designed system, where you can see the component blocks and the connections between them.

### Original Block Diagram
The original Block Diagram of the SAP-1 Computer can be found in the book "Digital Computer Electronics" by Albert Paul Malvino and Jerald A. Brown, on page 141 and is labeled Figure 10-1.

In the following figure, I present a reproduction of the original Block Diagram of the SAP-1 Computer.

![ Figure 1 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure1.png)

### More detailed Block Diagram
I studied the original schematic of the SAP-1 Computer and recreated the block diagram to represent the actual functional blocks as closely as possible and I present it in the following figure.

![ Figure 2 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure2.png)

The HLT control signal was omitted in the original Block Diagram.

The programming mode of the SAP-1 Computer described by the authors is as follows: \
a.	Move selector S2 to the PROG position to enter Programming Mode, \
b.	Select with the S1 switches the memory address whose content you want to modify, \
c.	Select with the S3 switches the Data that you want to be written to the memory at the previously set address, \
d.	Press button S4 to write the new value to memory, \
e.	Repeat steps b, c and d until all necessary changes have been made, \
f.	Move selector S2 to the RUN position, to run the program.

In practice, the content of the RAM memory is edited, after which its content is only read by the SAP-1 Computer.

This Computer has no instruction to write data to memory. This is specific to read-only ROMs. So, one ROM can be used for each program.

### Block Diagram where only active high control signals are used
In the Diagram in [Figure 2](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure2.png) it can be seen that some of the control signals are active high and some are active low. This is due to the fact that the circuit diagram is optimized for the TTL integrated circuits used by the authors of the original design of the SAP-1 Computer.

To simplify and ease the Control Block design process, I propose that in this phase of the design we only use active High control signals. This way, the Timing Diagrams in the chapter where we will study the Instruction Set will be easier to understand.

The Block Diagram where only active high control signals are used, can be seen in the following figure.

![ Figure 3 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure3.png)

### Identification of Computer Components
As we learned in school, a computer can be represented by 3 distinct functional blocks:
- CPU (Central Processing Unit),
- Memory,
- I/O (Inputs / Outputs).

They are interconnected through 3 buses that form the System Bus:
- Data Bus,
- Address Bus,
- Control Bus.

This fact is also presented by the authors in the Book in a simplified form on page 213 in figure 13-1.

A diagram representing a computing system consisting of functional blocks CPU, RAM, I/O and buses is presented in the following figure.

![ Figure 4 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure4.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W Bus".

So, I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. 
We get the following Block Diagram:

![ Figure 5 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure5.png)

### Separation of the Central Processing Unit
I propose separating the component blocks of the Central Processing Unit from the other blocks of the computer. This way we will be able to focus on improving the design of only the Central Processing Unit as an entity independent of the other constructive elements of the ISAP-1 Computer.

Thus, from [Figure 5](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure5.png) we will remove the following blocks:
- Address Select Switches,
- Program / Run Selector + Deposit,
- Data Select Switches,
- Address MUX,
- 16 x 8 RAM,
- Output Register,
- Binary Display,
- Clock and Reset,
- Power Supply.

The resulting Block Diagram is shown in the following figure:

![ Figure 6 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure6.png)

In order to highlight the three system buses, we must invert the positions of the Program Counter and the Memory Address Register in the diagram.

Now I have renamed the Memory Address Register as the Address Register

![ Figure 7 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure7.png)

The CE signal was renamed PM = Program Memory select \
The LM signal was renamed LAR = Load Address Register \
The LO signal was renamed I/O = Input/Output Device select.

### Control Unit structure
The SAP-1 computer has a Control Unit made using logic gates.

The Control Unit is built from three blocks:
- Instruction Decoder,
- Step Counter,
- Control Matrix.

The instruction decoder has the structure of a classic decoder and activates a single output depending on the instruction code presented at the input. The number of active outputs is equal to the number of instructions present in the Instruction Set.

The SAP-1 computer is based on micro-step control. For this purpose, a Step Counter block is required. The authors of the SAP-1 computer used a Ring Counter to implement the Step Counter.

The Control Matrix has the role of generating control signals depending on the instruction that is executed in accordance with the current micro-step.

![ Figure 8 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure8.png)

### Binary Display
The simplest output device that can be connected to this Computer is a Binary Display. This device is used in the original construction of the SAP-1 Computer, where it is integrated directly into the structure of this Computer.

My version of the Block Diagram is identical to the original, except that I treated the original Output Register as a standalone block that is connected to the system buses as an Input/Output Device.

The output device consists of a register where 8 bits are written when the I/O control signal is activated and the rising edge of the clock occurs. Each bit from the output of this register is connected to an LED. This is a Binary Display.

![ Figure 9 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure9.png)

### Memory Subsystem
The following figure shows the Memory block of the SAP-1 computer.

![ Figure 10 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure10.png)

The Memory has two operating modes, dictated by the position of switch S2.

When S2 is in the Run position, the PGM signal is low and causes the Address Multiplexer to select the address from the input connected to the Memory Address Register. Also, the CE control signal is connected to the #CE control pin of the RAM. The SAP-1 computer in this mode executes the program from memory.

The Diagram of the Memory Block in Run Mode is as follows

![ Figure 11 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure11.png)

