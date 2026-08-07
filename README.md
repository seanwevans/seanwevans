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
| [Bambusa](https://github.com/seanwevans/Bambusa) | 0 | 0 | A branchless programming language |
| [bird](https://github.com/seanwevans/bird) | 0 | 0 | a flight simulator |
| [Blast](https://github.com/seanwevans/Blast) | 0 | 0 | A high-throughput SQLite table dumper |
| [bomb-mopper](https://github.com/seanwevans/bomb-mopper) | 0 | 0 | minesweeper clone in react |
| [braggard](https://github.com/seanwevans/braggard) | 0 | 0 | Scrape a GitHub users' repositories and showcase them |
| [Capsule-UI](https://github.com/seanwevans/Capsule-UI) | 1 | 0 | A UI architecture enforcing component isolation via Shadow DOM and CSS Modules. Features zero-runtime styling, container queries, and seamless micro-frontend integration for React, Vue, and Svelte. |
| [CIPDGOL](https://github.com/seanwevans/CIPDGOL) | 0 | 0 | A cellular automaton simulator that evolves it into an organic, fluid system driven by influence propagation, decay, and survival mechanics. |
| [cordite](https://github.com/seanwevans/cordite) | 0 | 0 | how I've started jumpstarting my react apps recently |
| [Creative-Writing](https://github.com/seanwevans/Creative-Writing) | 0 | 0 | My Creative Writing Experiments |
| [Cromulent-PRNG](https://github.com/seanwevans/Cromulent-PRNG) | 0 | 0 | A perfectly cromulent, high-performance, modern 128-bit PRNG implemented in portable C, featuring scalar and AVX2-accelerated variants, comprehensive state management, and jump-ahead functionality. |
| [CV](https://github.com/seanwevans/CV) | 0 | 0 | Sean W. Evans |
| [Damnati](https://github.com/seanwevans/Damnati) | 0 | 0 | A CUDA-accelerated iterated prisoner's dilemma arena |
| [DeclarativeML](https://github.com/seanwevans/DeclarativeML) | 0 | 0 | a SQL-like declarative language for supervised learning |
| [EFC](https://github.com/seanwevans/EFC) | 0 | 0 | A toy theory in which spacetime is an emergent entropic field |
| [egg-file-format](https://github.com/seanwevans/egg-file-format) | 0 | 0 | The Egg File Format |
| [egg64](https://github.com/seanwevans/egg64) | 0 | 0 | A Nintendo 64 game about an Egg |
| [fhir-department](https://github.com/seanwevans/fhir-department) | 0 | 0 | 🔥A system for converting unstructured medical information into the Fast Healthcare Interoperability Resources (FHIR) format. |
| [flags-of-the-world](https://github.com/seanwevans/flags-of-the-world) | 0 | 0 | The flags of the world in css |
| [fluid-sims](https://github.com/seanwevans/fluid-sims) | 62 | 3 | Collection of high-performance, CUDA-accelerated fluid dynamics and physics simulators, including SPH, hypersonic flow, and reaction-diffusion systems. |
| [GDSL](https://github.com/seanwevans/GDSL) | 0 | 0 | A DSL that expresses GPU state transitions, command buffer composition, and VRAM residency semantics directly, in a vendor-neutral way. |
| [Geez-Ball](https://github.com/seanwevans/Geez-Ball) | 0 | 0 | clone of jezzball |
| [gh-status](https://github.com/seanwevans/gh-status) | 0 | 0 | Realtime status dashboard for GitHub build processes |
| [Ghast](https://github.com/seanwevans/Ghast) | 3 | 1 | Security auditing and remediation tool for GitHub Actions workflows that detects vulnerabilities, misconfigurations, and anti-patterns based on industry best practices. |
| [Image-Report](https://github.com/seanwevans/Image-Report) | 0 | 0 | Generate XML reports from image data. |
| [jsean](https://github.com/seanwevans/jsean) | 0 | 0 | A JSON-like data structure designed for granular access control, field-level encryption, and robust audit capabilities. |
| [kerinferencel](https://github.com/seanwevans/kerinferencel) | 0 | 0 | An implementation of MNIST digit recognition using eBPF. |
| [Latency-Mesh](https://github.com/seanwevans/Latency-Mesh) | 0 | 0 | Map the topology of your surrounding Internet |
| [libinflate](https://github.com/seanwevans/libinflate) | 0 | 0 | A simple implementation of the INFLATE (and DEFLATE) algorithm in pure JavaScript. |
| [lockstep](https://github.com/seanwevans/lockstep) | 12 | 0 | Data-oriented systems programming language for high-throughput, deterministic compute pipelines, enforcing a straight-line SIMD execution model and static memory topology for maximum CPU vectorization. |
| [mandelbros](https://github.com/seanwevans/mandelbros) | 0 | 0 | a variety of mandelbrot fractals |
| [me-spin](https://github.com/seanwevans/me-spin) | 0 | 0 | A simple single drop-in header UTF-8 text spinner library. |
| [MoQTail](https://github.com/seanwevans/MoQTail) | 0 | 0 | an XPATH-like language for MQTT |
| [Nagare](https://github.com/seanwevans/Nagare) | 0 | 0 | Continuous, Befunge-like programming language designed for simulating dynamic systems involving vector fields, spatial zones, and time-evolving entities. The project features a custom C/Python interpreter, tools for trajectory visualization, and an interactive web-based simulation player. |
| [ngipd](https://github.com/seanwevans/ngipd) | 0 | 0 | A Progressively-Deepening N-Gram Strategy for the Iterated Prisoner's Dilemma |
| [nlp-dump](https://github.com/seanwevans/nlp-dump) | 1 | 0 | Use Spacy to save out linguistic data in various formats. |
| [ombud](https://github.com/seanwevans/ombud) | 0 | 0 | A digital bureaucratic advocate that helps people navigate complex institutions like the DMV, hospitals, and courthouses with clarity, guidance, and empathy. |
| [OpenAstroViz](https://github.com/seanwevans/OpenAstroViz) | 0 | 0 | FlightRadar24 for space: open-source, physics-grade tracker and real-time visualizer for every object in Earth orbit. Democratizing space-situational awareness with a real-time, GPU-accelerated orbital map for satellites, spent stages, and space debris. |
| [opencv-playground](https://github.com/seanwevans/opencv-playground) | 0 | 0 | an opencv playground |
| [Oriel](https://github.com/seanwevans/Oriel) | 0 | 0 | Retro desktop simulation built with vanilla HTML, CSS, and JavaScript, featuring a diverse collection of integrated applications, classic games, and system utilities. |
| [pg_browser](https://github.com/seanwevans/pg_browser) | 0 | 0 | A browser in postgres |
| [pg_git](https://github.com/seanwevans/pg_git) | 1 | 0 | PostgreSQL-native Git implementation providing full version control functionality including core operations, branching, merging, and remote transport directly within the database.. |
| [pg_gpt2](https://github.com/seanwevans/pg_gpt2) | 3 | 0 | Complete implementation of the GPT-2 architecture entirely inside PostgreSQL, featuring a native tensor engine, autograd, and AdamW optimization for end-to-end training and inference via SQL. |
| [pg_os](https://github.com/seanwevans/pg_os) | 3 | 0 | PostgreSQL extension providing operating system-level functionality directly through SQL, enabling process management, file system operations, IPC, and system monitoring within the database environment. |
| [pg_shell](https://github.com/seanwevans/pg_shell) | 4 | 0 | Stateless, auditable, and replayable command shell built entirely on PostgreSQL and htmx. It replaces persistent shell processes with database-backed terminal sessions, where every command, output, and environment change is recorded in real-time. |
| [pg_ttd](https://github.com/seanwevans/pg_ttd) | 0 | 0 | openTTD clone in postgres |
| [pieman](https://github.com/seanwevans/pieman) | 0 | 0 | A simple, configurable neural network optimized using AVX. |
| [Pipe-Lion](https://github.com/seanwevans/Pipe-Lion) | 0 | 0 | Browser-first packet inspection playground. It pairs a high-performance WebAssembly-powered Rust core with a modern React/TypeScript web interface, allowing users to drag-and-drop .pcap or .pcapng files and analyze packet traces locally without a backend. |
| [PyIsolate](https://github.com/seanwevans/PyIsolate) | 0 | 0 | PyIsolate is a multi-tenant Python execution fabric built on free-threaded CPython, where subinterpreters become cheap, parallel execution cells and policy/runtime machinery makes them operationally usable. |
| [pynq_butterfly](https://github.com/seanwevans/pynq_butterfly) | 1 | 0 | FPGA accelerator for exact OpenFHE DCRTPoly polynomial multiplication in Z_q[X]/(X^4096+1), on a PYNQ-Z2 (XC7Z020) |
| [r3d](https://github.com/seanwevans/r3d) | 0 | 0 | A React-based 3D template |
| [raft-vm](https://github.com/seanwevans/raft-vm) | 2 | 0 | A lightweight VM designed to provide concurrency, fault tolerance, and actor-based message-passing models. |
| [SafeLang](https://github.com/seanwevans/SafeLang) | 0 | 0 | A language based on NASA's "The Power of 10: Rules for Developing Safety-Critical Code" |
| [sean](https://github.com/seanwevans/sean) | 0 | 0 | The de-facto primitives |
| [seanwevans](https://github.com/seanwevans/seanwevans) | 0 | 0 | sean |
| [Simon](https://github.com/seanwevans/Simon) | 0 | 0 | A multi-threaded web server. |
| [sme](https://github.com/seanwevans/sme) | 0 | 0 | A collection of mathematical experiments |
| [SpacyVis](https://github.com/seanwevans/SpacyVis) | 1 | 0 | XML annotation visualizer with interactive highlighting. |
| [SPdf](https://github.com/seanwevans/SPdf) | 0 | 0 | A lightweight implementation of a psuedo-pdf document. |
| [SpecStack](https://github.com/seanwevans/SpecStack) | 0 | 0 | Transform OpenAPI 3.0 specifications into PostgreSQL schemas with fully typed React Query hooks. |
| [Spreadsheet-Page-Description-Language](https://github.com/seanwevans/Spreadsheet-Page-Description-Language) | 0 | 0 | a spreadsheet page description language |
| [srxe](https://github.com/seanwevans/srxe) | 0 | 0 | A custom regular expression engine. |
| [stree](https://github.com/seanwevans/stree) | 0 | 0 | tree, but slower |
| [sysview](https://github.com/seanwevans/sysview) | 0 | 0 | Uses Ebpf to generate real-time visualizations from your syscalls |
| [Tag0](https://github.com/seanwevans/Tag0) | 0 | 0 | Implements type-tagged values based on an academic paper. |
| [Tensor-Ball](https://github.com/seanwevans/Tensor-Ball) | 0 | 0 | A massive-batch reinforcement learning environment in the browser. Trains a CNN agent to play basketball using Three.js, Cannon-es, and TensorFlow.js. |
| [testdata](https://github.com/seanwevans/testdata) | 0 | 0 | test data I've collected |
| [Totem](https://github.com/seanwevans/Totem) | 0 | 0 | A no-syntax-error programming language |
| [Tranche](https://github.com/seanwevans/Tranche) | 0 | 0 | Actuarial multi-CDN failover control plane that reroutes traffic off any CDN/edge provider during outages. |
| [transplant](https://github.com/seanwevans/transplant) | 0 | 0 | Recreate directory structures from tree's output |
| [TypeCrypt](https://github.com/seanwevans/TypeCrypt) | 0 | 0 | An encryption scheme where types are keys |
| [WarpDB](https://github.com/seanwevans/WarpDB) | 0 | 0 | GPU-accelerated SQL query engine that leverages CUDA JIT compilation to dynamically generate optimized kernels for high-performance analytical workloads and multi-GPU data processing. |
| [WaveSim](https://github.com/seanwevans/WaveSim) | 0 | 0 | A simple wave simulation in React |
| [Whelk](https://github.com/seanwevans/Whelk) | 0 | 0 | A toy proof-of-concept homomorphic encryption |
| [XORM](https://github.com/seanwevans/XORM) | 1 | 0 | ⊕, macros, and two 8-bit registers. That's all you get. |
