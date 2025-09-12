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
