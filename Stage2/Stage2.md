# Improved SAP Computer

## Stage 2 - Design improvement by analyzing and modifying the block diagram
The original Block Diagram of the SAP-1 computer can be found in the book "Digital Computer Electronics" by Albert Paul Malvino and Jerald A. Brown, on page 141 and is labeled Figure 10-1.

In the following figure, I present to you a reproduction of the block diagram of the SAP-1 computer.

![ Figure 1 ](/Pictures/Figure1.png)

I studied the original electronic schematic of the SAP-1 computer and recreated the block diagram to represent the actual functional blocks as closely as possible and I present it in the following figure.

![ Figure 2 ](/Pictures/Figure2.png)

As we learned at school, a computer can be represented by 3 distinct functional blocks: CPU, Memory and I/O. They are interconnected by 3 buses: the Data Bus, the Address Bus and the Control Bus.

This fact is also presented by the authors in the book in a simplified form on page 213 in figure 13-1.

A diagram representing a computing system consisting of functional blocks CPU, RAM, I/O and buses is presented in the following figure.

![ Figure 3 ](./Figure3.png)

If we check the diagram of the SAP-1 computer we notice that these functional blocks are not grouped, we also cannot identify the three buses on the diagram. We are presented with only the data bus labeled "W bus".

So I propose to redraw the Block Diagram of the SAP-1 computer so that we can easily separate these elements: CPU, RAM and I/O, as well as we can easily identify the three buses. We get the following block diagram.

![ Figure 4 ](./Figure4.png)

I presented a much more detailed version in the following figure.

![ Figure 5 ](./Figure5.png)

### Problem 1 - The computer cannot write to the RAM memory.
From the analysis of the block diagram, I found the first problem that the computer cannot store data in the RAM memory
so the current configuration only allows reading the contents of the RAM memory ROM-specific behavior.

The computer stores the result of arithmetic operations only in register A.