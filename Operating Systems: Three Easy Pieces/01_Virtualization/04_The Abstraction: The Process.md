The OS creates this illusion by **virtualizing** the CPU.

By running one process, then stopping it and running another, and so forth,

the OS can promote the illusion that many virtual CPUs exist when in fact there is only one physical CPU (or a few).

This basic technique, known as **time sharing** of the CPU, allows users to run as many concurrent processes as they would like;

the potential cost is performance, as each will run more slowly if the CPU(s) must be shared.

## 4.1 The Abstraction: A Process

A process is simply a running program.

Instructions lie in memory; the data that the running program reads and writes sits in memory as well.

Thus the memory that the process can address (called its **address space**) is part of the process.

Note that there are some particularly special registers that form part of this machine state.

For example, the **program counter (PC)** tells us which instruction of the program will execute next.

## 4.2 Process API

- Create
- Destroy
- Wait
- Miscellaneous Control
- Status

## 4.3 Process Creation: A Little More Detail

The first thing that the OS must do to run a program is to load its code and any static data (e.g., initialized variables) into memory, into the address space of the process.

Before running anything, this OS clearly must do some work to get the important program bits from disk into memory.

Some memory must be allocated for the program's **run-time stack** (or just **stack**).

C programs use the stack for local variables, function parameters, and return addresses; the OS allocates this memory and gives it to the process.

The OS may also allocate some memory for the program's **heap**.

In C programs, the heap is used for explicitly requested dynamically-allocated data; programs request such space by calling `malloc()` and free it explicitly by calling `free()`.

The heap is needed for data structures such as linked lists, hash tables, trees, and other interesting data structures.

The OS will also do some other initialization tasks, particularly as related to input/output (I/O).

For example, in UNIX systems, each process by default has three open **file descriptors**, for standard input, output, and error; these descriptors let programs easily read input from the terminal and print output to the screen.

By loading the code and static data into memory, by creating and initializing a stack, and by doing other work as related to I/O setup, the OS has now (finally) set the stage for program execution.
