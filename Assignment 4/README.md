# Assignment 4 - Pipelined Processor

In this assignment, we have modified the single cycled processor to a pipelined processor at the same time ensuring that data and control hazards were handled. The major changes were done to the latch type classes to incorporate locks that were used to perform data interlocks and control interlocks.

# Code Base

* configuration
  * Configuration.java
* generic
  * Instruction.java
  * Misc.java
  * Operand.java
  * Simulator.java - This file has been modified to ensure all the five stages occurs in a single cycle. The other functionalities of the file remain unchanged.
  * Statistics.java - This file has been modified to include other statistics like number of branches taken. Number of OF stage instructions, and number of RW stage instructions
* main
  * Main.java
* processor
  * Clock.java
  * Processor.java
  * memorysystem
    * MainMemory.java
  * pipeline
    * RegisterFile.java
    * IF_EnableLatchType.java
    * InstructionFetch.java
    * IF_OF_LatchType.java
    * OperandFetch.java - This file has been modified to ensure data hazards do not occur. While reading the values from the register, this stage checks if reading those values would cause a conflict. If a conflict occurs, then this stage would be idle in that cycle. Else it would function normally.
    * OF_EX_LatchType.java - This file has been modified to include an EX stage lock. Which will be used by other stages to lock the EX stage in case of a conflict.
    * Execute.java - This file has been modified to ensure it only runs in case it is not locked. This stage is locked whenever there is a conflict.
    * EX_MA_LatchType.java - This file has been modified to include an MA stage lock. Which will be used by other stages to lock the MA stage in case of a conflict.
    * MemoryAccess.java - This file has been modified to ensure it only runs in case it is not locked. This stage is locked whenever there is a conflict.
    * MA_RW_LatchType.java - This file has been modified to include an RW stage lock. Which will be used by other stages to lock the RW stage in case of a conflict.
    * RegisterWrite.java - This file has been modified to ensure it only runs in case it is not locked. This stage is locked whenever there is a conflict.
    * EX_IF_LatchType.java
