# Assignment 2 - ToyRISC ISA Assembler

An assembler is a program that takes a program code in the form of assembly language and converts it to a predefined binary pattern that can be used by the computer's processor. In this particular assignment, we have written an assembler for ToyRISC ISA. The output is an object file with binary code according to the given ISA specifications.

## Code base

The SRC folder has 3 directories inside: configuration, generic, and main

* configuration/Configuration.java - This particular file is used to configure the parameters and initial values for the assembler.

* generic/Instruction.java - This file defines the Instruction class, a typical instruction contains an opcode, or operation type, source operand 1, source operand 2, and destination operand, with setter and getter methods to access and modify those parameters.

* generic/Misc.java - This particular file has Misc class, which is used to exit the program when an error occurs.

* generic/Operand.java - This file defines the Operand class, a typical operand has operandtype, and its associated value, it also has getter and setter methods to access and modify these parameters.

* generic/ParsedProgram.java - This file defines the ParsedProgram class, which reads an instruction, and breaks it down into the corresponding opcode, registers and/or immediates, whichever is applicable. This aids in accessing the opcodes and operands from each instructions easily.

* generic/Simulator.java - This is the heart of the whole assembler. This program reads through every line of the given assembly code and converts them into corresponding binary structures.

* generic/Statistics.java - This file would be updated in further assignments, to be used to keep track for number of cycles, number of instructions etc.

* main/Main.java - This file defines the Main class, and starts the simulator.
