# Sean W. Evans

I build experimental systems at the boundary of **mathematics, high-performance computing, programming languages, databases, and machine learning**.

Most of my projects begin with a structural question:

**Can a different representation make this problem simpler, faster, safer, or possible at all?**

The result is usually a working system: a compiler, accelerator, simulation, database runtime, file format, protocol, or deliberately strange proof of concept.

My background is in production software and ML engineering. I am increasingly focused on research-oriented computing: algorithms, numerical systems, GPU/FPGA acceleration, compilers, and unconventional computational models.

Gists are located [here](https://gist.github.com/seanwevans/)

---

## Featured Work

### [pynq_butterfly](https://github.com/seanwevans/pynq_butterfly)

**Exact FPGA acceleration for homomorphic encryption**

An FPGA accelerator for OpenFHE BGVRNS ciphertext multiplication and BV relinearization on a PYNQ-Z2.

The project moves dense modular arithmetic and key-switch computation into RTL while preserving coefficient-exact compatibility with OpenFHE.

* Exact hardware implementation of ciphertext multiplication and BV relinearization
* Pipelined Barrett modular arithmetic
* AXI DMA transport and coefficient-major evaluation-key reuse
* Measured on physical PYNQ-Z2 hardware
* 6,291,456 residue comparisons against OpenFHE with zero mismatches
* 245.61 relinearized ciphertexts/sec in the current persistent-session design
* 98.84% of the calculated input transport ceiling at the measured batch size

The repository documents not just the final implementation, but the sequence of architectural changes that moved the design from 91 to 245 ciphertexts/sec.

---

### [Lockstep](https://github.com/seanwevans/lockstep)

**A systems language built around straight-line SIMD computation**

Lockstep is an experimental data-oriented programming language for deterministic, high-throughput compute pipelines.

Instead of treating a program as a sequence of arbitrary instructions, Lockstep models computation as a static graph of data transformations.

It includes:

* custom grammar and compiler frontend
* semantic type checking
* static memory topology
* Struct-of-Arrays layout
* explicit branchless compute kernels
* linear reduction types
* LLVM IR generation
* manual SIMD lowering
* generated C host interfaces
* pipeline simulation
* compiler diagnostics
* benchmark regression testing
* Language Server Protocol support

The experiment asks what a systems language looks like when predictable data movement and vector execution are architectural constraints rather than compiler afterthoughts.

---

### [fluid-sims](https://github.com/seanwevans/fluid-sims)

**CUDA numerical simulation laboratory**

A collection of GPU-accelerated physical and mathematical simulations implemented primarily in CUDA.

Experiments include:

* Smoothed Particle Hydrodynamics
* hypersonic flow
* reaction-diffusion systems
* 3-D fluid dynamics
* viscous Burgers flow
* shallow-water equations
* 2-D fluid solvers

The repository is a laboratory for numerical methods, GPU execution models, visualization, and the relationship between mathematical formulation and computational structure.

---

### [pg_gpt2](https://github.com/seanwevans/pg_gpt2)

**GPT-2 implemented entirely inside PostgreSQL**

A complete GPT-2 implementation in which PostgreSQL acts simultaneously as the model store, tensor runtime, computational graph, optimizer state store, and execution environment.

The system includes:

* native C tensor operations
* reverse-mode automatic differentiation
* relational autograd tape
* GPT-2 attention and feed-forward layers
* AdamW optimization
* BPE tokenization
* checkpointing
* training and inference
* SQL-driven text generation

Every model operation is represented through database state and transactions.

The larger experiment is whether a relational database can serve as a general computational runtime rather than merely storing inputs and outputs for one.

---

### [WarpDB](https://github.com/seanwevans/WarpDB)

**A GPU query engine that compiles data operations into CUDA**

WarpDB parses SQL-like expressions into an abstract syntax tree, generates CUDA code from the resulting representation, compiles kernels at runtime using NVRTC, and executes them directly against GPU-resident data.

It includes:

* expression parsing and AST generation
* CUDA kernel code generation
* runtime NVRTC compilation
* GPU filtering and projection
* column statistics and simple optimization
* Arrow integration
* Python bindings
* multi-GPU execution
* streaming execution for datasets larger than device memory

The central idea is simple: instead of building a large fixed set of GPU query operators, generate the computation required by the query itself.

---

### [4splat](https://github.com/seanwevans/4splat)

**An experimental lossless representation for spatiotemporal data**

4Splat explores an extension of indexed-color images into higher-dimensional image and video data.

Instead of treating every video frame independently, the format represents samples over spatial and temporal coordinates and indexes them through a shared palette of higher-dimensional splats.

The project includes:

* a binary `.4spl` format
* reference encoder and decoder
* explicit binary layout and versioning
* spatiotemporal indexing
* Gaussian splat representation
* lossless reconstruction

The broader question is whether representations normally associated with images can be generalized into useful structures over space-time.

---

## Other Experiments

The rest of this account is my working laboratory.

It includes:

**Programming languages & compilers**
branchless languages, safety-constrained languages, no-syntax-error languages, declarative ML languages, regular-expression engines, DSLs, interpreters, and unusual execution models.

**Databases & runtimes**
PostgreSQL-native Git, shells, operating-system interfaces, browsers, ML runtimes, schema compilers, and other experiments in treating the database as a computational substrate.

**GPU & parallel computing**
CUDA simulation, GPU databases, cellular automata, reinforcement-learning environments, cryptographic accelerators, and performance experiments.

**Distributed systems**
consensus experiments, actor-style VMs, distributed ML execution, failover systems, and network-topology tools.

**Low-level systems**
x86-64 assembly utilities, eBPF experiments, custom servers, binary formats, compression, PRNGs, and syscall-level tooling.

**Mathematical experiments**
fractals, dynamical systems, cryptography, simulation, alternate computational representations, and small mathematical investigations.

**Interesting Things**
games, civic software, weird interfaces, protocol tools, visualization experiments, and ideas that were worth implementing even when they had no obvious product attached.

---

## What I Like Working On

I am particularly interested in problems where the obvious implementation is too slow, too complicated, or based on the wrong abstraction.

That usually means some combination of:

* algorithms
* scientific computing
* high-performance computing
* GPU and FPGA acceleration
* compiler construction
* programming-language design
* numerical methods
* database internals
* distributed systems
* machine-learning infrastructure
* mathematical modeling
* unusual representations of computation

The recurring goal is to find the representation that makes the hard part easy.

---

## Project Index


| Repository | Stars | Forks | Description |
| ---------- | ----- | ----- | ----------- |
| [4splat](https://github.com/seanwevans/4splat) | 13 | 1 | Binary format and reference implementation for 4Splat (.4spl). Palette-based, lossless 4D video codec that generalizes indexed-color images to  spatiotemporal data with Gaussian splats |
| [Alinas-Playhouse](https://github.com/seanwevans/Alinas-Playhouse) | 0 | 0 | A dollhouse game |
| [an-ki](https://github.com/seanwevans/an-ki) | 2 | 0 | Distributed neural network project built with Rust that supports task scheduling, load balancing, and fault tolerance across a network of nodes. It leverages asynchronous operations, leader election, and health monitoring to ensure high availability and scalability for secure inter-node communication. |
| [Baloo](https://github.com/seanwevans/Baloo) | 0 | 0 | Collection of 150 essential UNIX utilities written in pure x86_64 assembly using direct syscalls. No libc, no dependencies, just the bear necessities of life. |
| [bird](https://github.com/seanwevans/bird) | 0 | 0 | a flight simulator |
| [Creative-Writing](https://github.com/seanwevans/Creative-Writing) | 0 | 0 | My Creative Writing Experiments |
| [egg-file-format](https://github.com/seanwevans/egg-file-format) | 0 | 0 | The Egg File Format |
| [fluid-sims](https://github.com/seanwevans/fluid-sims) | 62 | 3 | Collection of high-performance, CUDA-accelerated fluid dynamics and physics simulators, including SPH, hypersonic flow, and reaction-diffusion systems. |
| [gh-status](https://github.com/seanwevans/gh-status) | 0 | 0 | Realtime status dashboard for GitHub build processes |
| [Ghast](https://github.com/seanwevans/Ghast) | 3 | 1 | Security auditing and remediation tool for GitHub Actions workflows that detects vulnerabilities, misconfigurations, and anti-patterns based on industry best practices. |
| [lockstep](https://github.com/seanwevans/lockstep) | 12 | 0 | Data-oriented systems programming language for high-throughput, deterministic compute pipelines, enforcing a straight-line SIMD execution model and static memory topology for maximum CPU vectorization. |
| [Oriel](https://github.com/seanwevans/Oriel) | 0 | 0 | Retro desktop simulation built with vanilla HTML, CSS, and JavaScript, featuring a diverse collection of integrated applications, classic games, and system utilities. |
| [pg_gpt2](https://github.com/seanwevans/pg_gpt2) | 3 | 0 | Complete implementation of the GPT-2 architecture entirely inside PostgreSQL, featuring a native tensor engine, autograd, and AdamW optimization for end-to-end training and inference via SQL. |
| [pg_shell](https://github.com/seanwevans/pg_shell) | 4 | 0 | Stateless, auditable, and replayable command shell built entirely on PostgreSQL and htmx. It replaces persistent shell processes with database-backed terminal sessions, where every command, output, and environment change is recorded in real-time. |
| [PyIsolate](https://github.com/seanwevans/PyIsolate) | 0 | 0 | PyIsolate is a multi-tenant Python execution fabric built on free-threaded CPython, where subinterpreters become cheap, parallel execution cells and policy/runtime machinery makes them operationally usable. |
| [pynq_butterfly](https://github.com/seanwevans/pynq_butterfly) | 1 | 0 | FPGA accelerator for exact OpenFHE DCRTPoly polynomial multiplication in Z_q[X]/(X^4096+1), on a PYNQ-Z2 (XC7Z020) |
| [raft-vm](https://github.com/seanwevans/raft-vm) | 2 | 0 | A lightweight VM designed to provide concurrency, fault tolerance, and actor-based message-passing models. |
| [sean](https://github.com/seanwevans/sean) | 0 | 0 | The de-facto primitives |
| [Spreadsheet-Page-Description-Language](https://github.com/seanwevans/Spreadsheet-Page-Description-Language) | 0 | 0 | a spreadsheet page description language |
| [Tensor-Ball](https://github.com/seanwevans/Tensor-Ball) | 0 | 0 | A massive-batch reinforcement learning environment in the browser. Trains a CNN agent to play basketball using Three.js, Cannon-es, and TensorFlow.js. |
| [WarpDB](https://github.com/seanwevans/WarpDB) | 0 | 0 | GPU-accelerated SQL query engine that leverages CUDA JIT compilation to dynamically generate optimized kernels for high-performance analytical workloads and multi-GPU data processing. |
