# Performance Optimization

## Notes from High Performance Python
- A computer is made up of 3 primary components:
  - **computing units (e.g., CPU, GPU)**: how many computations/second
    - a computing unit takes in a series of bits and outputs another set of bits
    - property of interest:
      - number of operations/cycle: measured by its instructions/cycle (IPC)
      - number of cycles/second: measured by its clock speed
      - Vectorization occurs when a CPU is provided with multiple pieces of data at a time and can operate on all of them -> single instruction, multiple data (SIMD).
      - Hyperthreading: a virtual second CPU that hosts the OS + clever hardware logic tries to interleave 2 threads of instructions into the execution units on a single CPU.
      - Out-of-order execution: allows a compiler to spot that some parts of a linear program sequence do not depend on the results of a previous piece of work, which could occur in any order or at the same time -> greater utilization of resources.
      - Amdahl's law: "if a program designed to run on multiple cores has some subroutines that must run on one core, this will be the limitation for the maximum speedup that can be achieved by allocating more cores."
      - Python uses a _global interpreter lock (GIL)_, which makes sure a Python process can **run only one instruction at a time**, regardless of the number of cores. 
  - **memory units (e.g., RAM)**: how much data it can hold/_how fast_ we can read from and write to it
    - sequential read vs. random data
    - latency: the time it takes the device to find the data that is being used. "For a spinning hard drive, this latency can be high because the disk needs to physically spin up to speed, and the read head must move to the right position. On the other hand, for RAM, this latency can be quite small because everything is solid state."
    - in terms of capacity: HHD > SSD > RAM > L1/L2 cache
    - in terms of speed: HHD < SSD < RAM < L1/L2 cache
    - inverse relationship between capacity and speed. "Because of this, many systems implement a tiered approach to memory: data starts in its full state in the hard drive, part of it moves to RAM, and then a much smaller subset moves to the L1/L2 cache."
  - communication layers: how fast data is moved from one place to another
    - frontside bus: connection between RAM and the L1/L2 cache.
    - _getting data into and out of the GPU can be quite a taxing operation_ -> heterogeneous computing that combines both CPU and GPU
    - network: "network communications are generally much slower than the other types of communications".
    - "when chips are placed close to one another, the length of the physical wires joining them is smaller, which can allow for faster transfer speeds"
- JIT (just-in-time compiler)
- important tools and stable libraries in python
  - `io`: all sorts of IO for bytes, strings, and all the encodings
  - `array`: memory-efficient arrays for primitive types
  - `math`: basic math operations
  - `collections`: a wide variety of objects, including a deque, counter, and dictionary variants
  - `asyncio`: concurrent support for I/O-bound tasks using async and await syntax
- "Writing high performance code is only one part of being highly performant with successful projects over the longer term. Overall team velocity is far more important than speedups and complicated solutions. Several factors are key to this—good structure, documentation, debuggability, and shared standards."
- "optimizing for the team rather than the code block"
### 

