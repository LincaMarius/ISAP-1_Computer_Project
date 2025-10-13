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

![ Figure 3 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure3.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W Bus".

So, I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. 
We get the following Block Diagram:

![ Figure 4 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure4.png)

### Control Unit structure
The SAP-1 computer has a Control Unit made using logic gates.

The Control Unit is built from three blocks:
- Instruction Decoder,
- Step Counter,
- Control Matrix.

The instruction decoder has the structure of a classic decoder and activates a single output depending on the instruction code presented at the input. The number of active outputs is equal to the number of instructions present in the Instruction Set.

The SAP-1 computer is based on micro-step control. For this purpose, a Step Counter block is required. The authors of the SAP-1 computer used a Ring Counter to implement the Step Counter.

The Control Matrix has the role of generating control signals depending on the instruction that is executed in accordance with the current micro-step.

![ Figure 5 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure5.png)

### Binary Display
The simplest output device that can be connected to this Computer is a Binary Display. This device is used in the original construction of the SAP-1 Computer, where it is integrated directly into the structure of this Computer.

My version of the Block Diagram is identical to the original, except that I treated the original Output Register as a standalone block that is connected to the system buses as an Input/Output Device.

The output device consists of a register where 8 bits are written when the I/O control signal is activated and the rising edge of the clock occurs. Each bit from the output of this register is connected to an LED. This is a Binary Display.

![ Figure 6 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure6.png)

### Memory Subsystem
The following figure shows the Memory block of the SAP-1 computer.

![ Figure 7 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure7.png)

The Memory has two operating modes, dictated by the position of switch S2.

When S2 is in the Run position, the /PGM signal is low and causes the Address Multiplexer to select the address from the input connected to the Memory Address Register. Also, the /CE control signal is connected to the /CE control pin of the RAM. The SAP-1 computer in this mode executes the program from memory.

The Diagram of the Memory Block in Run Mode is as follows

![ Figure 8 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure8.png)

From this Diagram the Multiplexer can be ignored and we can obtain a simpler and easier to understand Diagram.

![ Figure 9 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure9.png)

Thus, the Memory of the SAP-1 Computer in Run Mode is used as a ROM memory. Control input /CE if high disables the output which is three-state, and if low at the output, the data from the address selected by the Memory Address Register is presented on the Bus.

In this case, the /CE control signal has the #CE function for chip activation but also the #OE (Output Enable) function specific to ROM memories.

When switch S2 is in the “Program” Position, the /PGM signal is high and causes the Address Multiplexer to select the address from the input connected to Address Select Switches S1.

The control input /CE is set low, so at the Memory output, the Data from the Address selected by the Address Select Switches S1 are presented on the Bus.

If the S4 (Deposit) switch is pressed, the /W control signal is set to the low value, which causes the Data present at the input pins whose values are set by the switches marked S3 (Data Select Switches) to be written to the Selected Address.

The Block Diagram of the Memory Block in Programming Mode is as follows

![ Figure 10 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure10.png)

From this Diagram the Multiplexer can be ignored and we can obtain a simpler and easier to understand Diagram.

![ Figure 11 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure11.png)

Since no Data is read from the Bus, so no Data is transferred to the Bus, this can also be ignored.

![ Figure 12 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure12.png)

We can conclude that in programming mode the Memory is functionally separate from the SAP-1 computer.

So, functionally speaking, the Memory is simply a ROM for the SAP-1 computer.

We can synthesize a Block Diagram for the Memory Subsystem of the SAP-1 and ISAP-1 computers

![ Figure 13 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure13.png)

We can see an increased complexity of the Memory Subsystem imposed by the need to modify the contents of the Memory using the Control Panel switches.

### Reset Circuit
The Reset circuit has the role of bringing the computer back to its initial state. Internally, the Central Processing Unit initializes the functional blocks so that they can begin stable execution of any program.

The block diagram of the reset circuit is shown in the following figure

![ Figure 14 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure14.png)

The circuit consists of a switch marked S5 with two positions followed by a debouncing circuit consisting of an RS flip-flop in the case of the SAP-1 computer.

### Clock Signal Generator circuit
The clock signal is responsible for ensuring synchronous operation of the computer, so that any action takes place at a precise moment in time. Through synchronization, data transfer in the system occurs in a controlled manner.

The SAP-1 computer has two operating modes:
- Manual – in this mode the clock signal is generated by pressing a button and the program execution advances step by step,
- Automatic – in this mode the clock signal is generated continuously and the program execution is continuous.

For the Automatic mode, the clock signal is generated by an oscillator made with an astable. Its output reaches a T-type flip-flop. The T-type flip-flop divides the input frequency by 2 but we also obtain a signal duty cycle of 50%.

To generate the clock signal in step-by-step mode, we have a two-position switch marked S6 in the diagram followed by an RS-type flip-flop which acts as a debouncing circuit.

The switch marked S7 in the schematic is used to select the operating mode. This is followed by an RS type flip-flop which acts as a debouncing circuit.

Depending on the chosen operating mode, one of the two clock signals is selected using a multiplexer.

The output of the multiplexer is taken by the buffer. Its role is to ensure the necessary fanout because the clock signal reaches all the functional blocks of the computer.

![ Figure 15 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure15.png)

The HLT input inhibits the clock signal when the computer has executed the HALT instruction.

### SAP-1 Computer architecture
The architecture of the SAP-1 computer up to this point is as follows:

![ Figure 16 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure16.png)

We can distinguish the three subsystems of the computer:
- The SAP-1 CPU
- The Memory Subsystem
- Inputs/Outputs Subsystem

They are interconnected through the three buses:
- 4-bit Address Bus
- 8-bit Data Bus
- 7-bit Control Bus

The available address space for the SAP-1 computer in this structure is:
- 16 bytes of Program Memory
- 1 Output Devices

The original Instruction Set of the SAP-1 computer is:
| Mnemonic | Opcode | Operation                                  |
|----------|--------|--------------------------------------------|
| LDA      | 0000   | Load RAM data into Accumulator             |
| ADD      | 0001   | Add RAM data to Accumulator                |
| SUB      | 0010   | Substract RAM data from Accumulator        |
| OUT      | 1110   | Load Accumulator data into Output Register |
| HLT      | 1111   | Stop processing                            |

From the analysis carried out so far we can draw the following conclusions:
- the Size of Programs that can be run is only 16 bytes,
- the SAP-1 Computer cannot retain the values of some variables because it cannot write to Memory,
- jumps in the program cannot be made to perform repetitive tasks because it cannot be written to the Program Counter,
- the SAP-1 Computer does not have a Stack, so program subroutines cannot be called,
- there is no input device that allows manual data entry.


## Instruction Set Analysis

### SAP-1 Computer Instruction Format
The original format of the SAP-1 computer instructions is:

| 4 bits instruction code   | 4 bits operand (memory address)          |
|---------------------------|------------------------------------------|

We notice that the upper nibble is used to encode an instruction. 
So, any instruction is encoded on 4 bits. 
Thus, we can have a maximum of 2 ^ 4 = 16 instructions.


### The Instruction Set of the SAP-1 computer
The original instruction set of the SAP-1 computer is:

| Mnemonic  | Opcode | Operation                                  |
|-----------|--------|--------------------------------------------|
| LDA n     | 0000   | Load RAM data into Accumulator             |
| ADD n     | 0001   | Add RAM data to Accumulator                |
| SUB n     | 0010   | Substract RAM data from Accumulator        |
| OUT *     | 1110   | Load Accumulator data into Output Register |
| HLT *     | 1111   | Stop processing                            |

We can see that the following opcodes: 0011, 0100, 0101, 0110, 0111, 1000, 1001, 1010, 1011, 1100, 1101 are not used. So, we can add 11 more new instructions.

These codes are treated by the SAP-1 computer as NOP instructions, the previous table can be completed as follows:

| Mnemonic | Opcode | Operation                                  |
|----------|--------|--------------------------------------------|
| LDA      | 0000   | Load RAM data into Accumulator             |
| ADD      | 0001   | Add RAM data to Accumulator                |
| SUB      | 0010   | Substract RAM data from accumulator        |
| NOP      | 0011   | No Operation                               |
| NOP      | 0100   | No Operation                               |
| NOP      | 0101   | No Operation                               |
| NOP      | 0110   | No Operation                               |
| NOP      | 0111   | No Operation                               |
| NOP      | 1000   | No Operation                               |
| NOP      | 1001   | No Operation                               |
| NOP      | 1010   | No Operation                               |
| NOP      | 1011   | No Operation                               |
| NOP      | 1100   | No Operation                               |
| NOP      | 1101   | No Operation                               |
| OUT      | 1110   | Load Accumulator data into Output Register |
| HLT      | 1111   | Stop processing                            |

*This is the complete Instruction Set for the SAP-1 computer and for the ISAP-1 computer version 1.0*

So we have the instructions encoded in the first 4 bits, leaving the next 4 bits for encoding the instruction parameter which represents a memory address where the operand is located in the case of the SAP-1 computer.

The SAP-1 computer executes an instruction in multiple steps called “Microsteps”.

Their number is chosen to allow the complete execution of the most complex instruction.

The SAP-1 computer needs 6 “Steps” to execute the ADD and SUB instructions.

Any Instruction has a FETCH portion, during which it is loaded from RAM into the Instruction Register, followed by the actual execution portion of the instruction.

### NOP instruction – No OPeration
Binary form:  **** **** \
Operation:  no operation \
Example: NOP

The NOP instruction has only the Fetch portion (present in all instructions), but has nothing in the execution portion of the instruction.

The NOP instruction is not included in the SAP-1 computer's Instruction Set but must be studied because, as we have shown previously, the codes 03h to 0Dh are equivalent to the NOP instruction for the SAP-1 computer.

The original timing diagram for the NOP instruction of the SAP-1 computer is:

![ Figure 17 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure17.png)

ALL UNIMPLEMENTED INSTRUCTIONS WILL BE TREATED BY THE ISP-1 CPU AS A NOP INSTRUCTION!

All instructions of the SAP-1 computer are executed in 6 steps noted in the diagram and wiring diagram T1 - T6. The first 3 steps are the Fetch portion and the last 3 are the Execution portion of the instruction. The Fetch part of the statement is identical for all instructions. The Execution part is specific to each individual instruction.

We can summarize the value of the control signals over time presented in these diagrams in the following table:

![ Table 1 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table1.png) 

Signals represented in Red: are active when data is written to the Data BUS \
Signals represented in Green: are active when reading data from the Data BUS \
Signals shown in Black: their activation has no influence on the Data BUS

If we put all the output signals on columns and highlight the control signals used by the NOP instruction we obtain the Truth Table for the NOP instruction for the SAP-1 computer.

![ Table 2 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table2.png) 

*If we implement the Control Block using a ROM memory, the data in this table will be used to realize its content.*

The Boolean equations for the signals that are active when the NOP instruction is executed for computer SAP-1 are:
-	EP = NOP * T1
-	LAR = NOP * T1
-	CP = NOP * T2
-	PM = NOP * T3
-	LI = NOP * T3

Since steps T1, T2 and T3 are present and identical in any instruction we can say that they are independent of the executed instruction so we can rewrite the instructions as follows:
-	EP = T1
-	LAR = T1
-	CP = T2
-	PM = T3
-	LI = T3

*If we implement the Control Block using Combinational Logic we will use these equations.*

### LDA instruction – LoaD the Accumulator
Binary form:  0000 nnnn \
Operation:  A ← [n] \
Example: LDA 9h

Loads the numeric value from Address [n] into the Accumulator.

The timing diagram for the LDA instruction implemented on SAP-1 Computer is as follows:

![ Figure 18 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure18.png)

We can summarize the value of the control signals over time presented in these diagrams in the following table:

![ Table 3 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table3.png) 

Signals represented in Red: are active when data is written to the Data BUS \
Signals represented in Green: are active when reading data from the Data BUS \
Signals shown in Black: their activation has no influence on the Data BUS

If we put all the output signals on columns and highlight the control signals used by the LDA instruction we obtain the Truth Table for the LDA instruction for the SAP-1 computer.

![ Table 4 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table4.png) 

*If we implement the Control Block using a ROM memory, the data in this table will be used to realize its content.*

The Boolean equations for the signals that are active when the LDA instruction is executed for computer SAP-1 are:
-	EP = T1
-	LAR = T1 + LDA * T4
-	CP = T2
-	PM = T3 + LDA * T5
-	LI = T3
-	EI = LDA * T4
-	LA = LDA * T5

*If we implement the Control Block using Combinational Logic we will use these equations.*

### ADD instruction – ADD to accumulator
Binary form:  0001 nnnn\
Operation:  A ← A + [n]\
Example: ADD 8h

Adds the numeric value at address [n] with the numeric value stored in the Accumulator and stores the result in the Accumulator.

The timing diagram for the ADD instruction implemented on SAP-1 Computer is as follows:

![ Figure 19 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure19.png)

We can summarize the value of the control signals over time shown in these diagrams in the following table:

![ Table 5 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table5.png) 

Signals represented in Red: are active when data is written to the Data BUS. \
Signals represented in Green: are active when reading data from the Data BUS. \
Signals shown in Black: their activation has no influence on the Data BUS.

If we put all the output signals on columns and highlight the control signals used by the ADD instruction we obtain the Truth Table for the ADD instruction for the SAP-1 computer.

![ Table 6 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Tables/Table6.png) 

*If we implement the Control Block using a ROM memory, the data in this table will be used to realize its content.*

The Boolean equations for the signals that are active when the ADD instruction is executed for computer SAP-1 are:
-	EP = T1
-	LAR = T1 + ADD * T4
-	CP = T2
-	PM = T3 + ADD * T5
-	LI = T3
-	EI = ADD * T4
-	LB = ADD * T5
-	EU = ADD * T6
-	LA = ADD * T6

*If we implement the Control Block using Combinational Logic we will use these equations.*

### SUB Instruction – SUBtract from accumulator
Binary form:  0010 nnnn \
Operation:  A ← A – [n] \
Example: SUB 5h

Subtracts the numeric value at Address [n] from the numeric value stored in the Accumulator and stores the result in the Accumulator.

The timing diagram for the SUB instruction implemented on SAP-1 Computer is as follows:

![ Figure 20 ](https://github.com/LincaMarius/ISAP-1_Computer_Project/blob/main/SAP-1_Computer/Pictures/Figure20.png)

