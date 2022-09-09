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
  * Processor.java - This file defines the Processor class, which combines all of the different parts of a processor such as registers, main memory, latches and the five different stages. All of the above parts are themselves defined as seperate class which are discussed later on. Along with these members, the Processor class also contains setter and getter methods to access and modify all those methods.
  * Clock.java - This file defines the Clock class, which is an abstraction of a clock used by actual processors.
  * memorysystem
    * MainMemory.java - This files defines the MainMemory class, which is an abstraction of the main memory used by the processor. Here it has a capacity of 2^16 = 65536 bytes.
  * pipeline
    * RegisterFile.java - This file defines the RegisterFile class, which is an abstraction to the registers in the program counter (PC), used by the processor. There are 32 registers and a program counter defined in this file, along with these, there are also setter and getter methods to access and modify those members.
    * IF_EnableLatchType.java - This file defines a class which dictates whether the Instruction Fetch (IF) stage is enabled or not.
    * InstructionFetch.java - This file defines the InstructionFetch stage, which, while enabled, fetches the instruction which is pointed to by the program counter (PC), and copies it to the IF-OF latch.
    * IF_OF_LatchType.java - This file defines a class which dictates whether the Operand Fetch (OF) stage is enabled or not. It also acts as a mechanism to parse the instruction from IF stage to the OF stage.
    * OperandFetch.java - This file defines the OperandFetch stage, which, while enabled, fetches the instruction from the IF-OF latch, disassembles it into the opcode and operands, and copies it to the OF-EX latch.
    * OF_EX_LatchType.java - This file defines a class which dictates whether the Execute (EX) stage is enabled or not. It also acts as a mechanism to parse opcodes and operands to the EX stage.
    * Execute.java - This file defines the Execute stage, which, while enabled, fetches the opcodes and operands from the OF-EX latch, and performs the corresponding arithmetic operation according to the opcode, on the operands, and copies the arithmetic results and the instruction to the EX-MA latch.
    * EX_MA_LatchType.java - This file defines a class which dictates whether the Memory Access (MA) stage is enabled or not. It also acts as a mechanism to parse the arithmetic result and the instruction to the MA stage.
    * MemoryAccess.java - This file defines the Memory Access (MA) stage, which, while enabled, fetches the arithmetic result and the instruction from the EX-MA latch and then accesses the memory location with the value of the arithmetic result only in the case of load and store operations. It also copies the arithmetic result, instruction and the load result (if needed) to the MA-RW latch.
    * MA_RW_LatchType.java - This file defines a class which dictates whether the Register Write (RW) stage is enabled or not. It also acts as a mechanism to parse arithmetic result, instruction and load result to the RW stage.
    * RegisterWrite.java - This file defines the Register Write (RW) stage, which, while enabled, fetches the arithmetic result, instruction and the load result from the MA-RW latch, and modifies register values if needed, in accordance with the instruction.
    * EX_IF_LatchType.java - This file defines a class which dictates whether the IF stage is enabled or not. It is used in case of JUMP instructions, and it works by copying the PC value from the EX stage to IF stage.
  
