# Assignment 3 - Single Cycle Processor Simulator

In this assignment, we have built a a single cycle processor simulator with five stages which are as follows.

* Instruction Fetch (IF) - This stage fetches one instruction line from a memory.
* Operand Fetch (OF) - This stage disassembles the instructions to get the opcode and operands.
* Execute (EX) - This stage performs the arithmetic operations.
* Memory Access (MA) - Any operations that alters memory are performed in this stage.
* Register Write (RW) - Any operations that alters register values are performed in this stage.

For communication between two stages, **latches** are used. They are as follows:

* IF-OF Latch
* OF-EX Latch
* EX-MA Latch
* MA-RW Latch
* EX-IF Latch

The processor also uses an abstraction of main memory to get the code as well as store the end results. It runs every instruction through the five stages described above, and modifies the main memory accordingly.

## Code Base

* generic
  * Instruction.java 
  * Misc.java
  * Operand.java
  * Simulator.java - This file has been modified to load the program from assembly code to the main memory, setup the simulation and start simulating the processor. At the same time, it also counts the number of instructions processed and the number of cycles used.
  * Statistics.java - This file defines the Statistics class that keeps track of the number of instructions executed and the number of cycles taken. It also has the required getter and setter functions required to access and modify those members.
* main
 * Main.java
* processor
 * Processor.java
  
