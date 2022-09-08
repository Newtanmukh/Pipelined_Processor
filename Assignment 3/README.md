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
  * Simulator.java - This file has been modified 
  * Statistics.java
