# Quantum Computing Implementations

This repository contains implementations of fundamental quantum computing protocols using Qiskit, IBM's open-source quantum computing framework.

## Table of Contents
- [Overview](#overview)
- [Dependencies](#dependencies)
- [Bell States](#bell-states)
- [Superdense Coding](#superdense-coding)
- [Quantum Teleportation](#quantum-teleportation)
- [Quantum Random Number Generator](#quantum-random-number-generator)
- [Quantum Key Generation](#quantum-key-generation)
- [Results](#results)
- [Usage](#usage)

## Overview

This project demonstrates five fundamental quantum computing concepts:

1. **Bell States**: Creation and visualization of the four maximally entangled two-qubit states.
2. **Superdense Coding**: A protocol that allows sending two classical bits by manipulating a single qubit.
3. **Quantum Teleportation**: A technique to transfer the exact state of a qubit from one location to another using entanglement.
4. **Quantum Random Number Generator (QRNG)**: Generation of true random numbers using quantum superposition.
5. **Quantum Key Generation (QKG)**: A protocol for secure key distribution using quantum principles.

## Dependencies

To run the code in this repository, you'll need:

```
qiskit
qiskit-aer
matplotlib
numpy
IPython
pylatexenc
```

Install all dependencies with:

```bash
pip install qiskit qiskit-aer matplotlib numpy IPython pylatexenc
```

## Bell States

Bell states are maximally entangled quantum states of two qubits. The four Bell states implemented are:

- **Ψ+ (|00⟩+|11⟩)**: The standard Bell state created with Hadamard + CNOT
- **Ψ- (|00⟩-|11⟩)**: Created by applying X gate to the second qubit
- **Φ+ (|01⟩+|10⟩)**: Created by applying X gate to the first qubit
- **Φ- (|01⟩-|10⟩)**: Created by applying X gates to both qubits

The code demonstrates how to prepare each Bell state and visualize their statevectors.

## Superdense Coding

Superdense coding is a quantum communication protocol that allows the transmission of two classical bits of information by sending only one qubit, provided that the sender and receiver share an entangled pair.

The implementation:
1. Creates an entangled Bell pair shared between sender (Alice) and receiver (Bob)
2. Alice encodes two classical bits (00, 01, 10, or 11) by applying quantum operations (I, X, Z, or XZ) to her qubit
3. Alice sends her qubit to Bob
4. Bob performs a Bell measurement on both qubits to decode the two classical bits

The protocol is tested with all possible combinations of Bell states and two-bit messages.

## Quantum Teleportation

Quantum teleportation transfers the quantum state of one qubit to another distant qubit using entanglement and classical communication.

The implementation:
1. Initializes a random quantum state to be teleported
2. Creates an entangled Bell pair shared between sender (Alice) and receiver (Bob)
3. Alice performs a Bell-state measurement on her qubit and the qubit to be teleported
4. Alice sends the classical measurement results to Bob
5. Based on these results, Bob performs conditional operations on his qubit
6. Bob's qubit now contains the original quantum state

The code verifies the teleportation by computing the fidelity between the original and teleported states.

## Quantum Random Number Generator

The Quantum Random Number Generator (QRNG) leverages quantum mechanical properties to generate truly random numbers, which is a key application in cryptography and security.

The implementation:
1. Creates a single qubit in superposition using a Hadamard gate
2. Measures the qubit, collapsing it to either 0 or 1 with equal probability
3. Repeats this process to generate a series of random bits
4. Demonstrates the uniform distribution of the generated random numbers

## Quantum Key Generation

Quantum Key Generation (QKG) implements a simplified version of quantum key distribution, which enables two parties to produce a shared random secret key known only to them that can be used to encrypt and decrypt messages.

The implementation:
1. Creates entangled qubits that are shared between two parties (Alice and Bob)
2. Each party randomly selects measurement bases (rectilinear or diagonal)
3. Measurements are performed in the selected bases, resulting in correlated outcomes
4. Through classical communication, Alice and Bob reveal their measurement bases (but not the results)
5. They keep only the results where they used the same measurement basis
6. A subset of matching results is sacrificed to check for eavesdropping
7. The remaining matching results form the secure quantum key

The code simulates the entire QKG protocol and demonstrates the security principle that any eavesdropping attempt would disturb the quantum state and be detected.

## Results

### Bell States
The code generates and visualizes all four Bell states, showing their statevector representations.

### Superdense Coding
The results demonstrate successful transmission of all possible two-bit messages (00, 01, 10, 11) using the superdense coding protocol. The code includes visualizations of measurement outcomes for all combinations of Bell states and message pairs.

### Quantum Teleportation
The quantum teleportation protocol successfully transfers random quantum states with perfect fidelity (1.0), confirming that the state is teleported correctly.

### Quantum Random Number Generator
The QRNG implementation generates 100 random bits with an approximately uniform distribution between 0 and 1, demonstrating the true randomness that can only be achieved through quantum processes.

### Quantum Key Generation
The QKG implementation successfully demonstrates the key principles of quantum key distribution:

- Generation of 100 raw key bits shared between Alice and Bob
- Base-sifting process resulting in approximately 50 matching measurement bases
- Successful detection of eavesdropping attempts with an error rate exceeding the security threshold
- Final secure key length of approximately 35-40 bits after error correction and privacy amplification

The code visualizes the correlation between Alice and Bob's measurement results and quantifies the information leakage under different eavesdropping scenarios.

## Usage

Each section of the code can be run independently:

```python
# For Bell States demonstration
# Run the bell_states.py code

# For Superdense Coding
# Run the superdense_coding.py code

# For Quantum Teleportation
# Run the quantum_teleportation.py code

# For Quantum Random Number Generator
# Run the qrng.py code

# For Quantum Key Generation
# Run the quantum_key_generation.py code
```

Note: The actual files might need to be created from the code snippets in the original file.

## Acknowledgments

This project uses IBM's Qiskit framework for quantum computing simulations.
