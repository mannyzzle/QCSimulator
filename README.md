# QCSimulator: Quantum Computation Simulator

QCSimulator is a comprehensive quantum computation simulator featuring multiple simulation engines:
	•	Statevector Simulator: An optimized simulator that surpasses the basic matrix multiplication approach.
	•	Matrix Product State Simulator: Implements a simple 1D tensor network with qubits arranged in a chain.
	•	Clifford Gates Simulator: Utilizes the stabilizer formalism to efficiently simulate Clifford circuits.

⸻

## Implemented Algorithms

Quantum Algorithms
	•	Grover’s Search
	•	Deutsch–Jozsa
	•	Simon
	•	Quantum Fourier Transform
	•	Phase Estimation
	•	Shor’s Factoring
	•	Bernstein–Vazirani
	•	Quantum Counting
	•	Quantum Teleportation
	•	Entanglement Swapping
	•	Superdense Coding
	•	Quantum Cryptography (BB84 Protocol)
	•	CHSH Inequality Violation

## Quantum Error Correction
	•	3-Qubit Bit-Flip Correction
	•	3-Qubit Phase-Flip Correction
	•	Shor Code

## Quantum Adders
	•	1-Qubit Quantum Half-Adder
	•	1-Qubit Quantum Full-Adder
	•	Full Adder for Two N-Qubit Numbers
	•	Draper Adder
	•	Draper Adder with Carry

## Simulation of Quantum Dynamics
	•	Hamiltonian Evolution: Simulate time evolution with a Hamiltonian expressed as a sum of Pauli product operators.
	•	1D Schrödinger Equation: Evolve a Gaussian packet in time using a Trotter decomposition combined with a Quantum Fourier Transform.

## Paradoxical Quantum Phenomena
	•	Quantum Eraser
	•	Elitzur–Vaidman Bomb Tester / Interaction-Free Measurement / Counterfactual Computation
	•	Hardy’s Paradox

## Quantum Games
	•	Coin Flipping
	•	Quantum Pseudo-Telepathy: The Magic Square Game

## Distributed Quantum Computing
	•	Distributed CNOT: Supports any 2-qubit controlled gate distribution.
	•	Quantum CNOT Gate Teleportation

## Quantum Machine Learning
	•	2D Q-Means Clustering

## Optimization Techniques
	•	QAOA: Quantum Approximate Optimization Algorithm on the Ising Model.
	•	VQE: Variational Quantum Eigensolver.

⸻

## Getting Started

To use QCSimulator in your project:
	1.	Include Directories:
Add the Eigen directory and the QCSim project directory (containing the source files) to your project’s include paths.
	2.	Compilation:
Compile your project with at least C++17.
	3.	Build System:
For Linux or macOS, it is recommended to use the provided CMake configuration. Enabling OpenMP can significantly boost performance, and if your system supports AVX2 (note: not available on Apple’s Metal), further speed improvements can be expected.

## Minimal Code Example

Here’s a simple example demonstrating how to initialize a 3-qubit register, apply a Pauli-X gate, and measure the outcome:

#include <iostream>
#include "QubitRegister.h"

int main() {
    // Create a 3-qubit register
    QC::QubitRegister reg(3);
    
    // Apply a Pauli-X gate to the first qubit
    QC::Gates::PauliXGate x;
    reg.ApplyGate(x, 0);
    
    // Measure all qubits
    unsigned int m = reg.MeasureAll();
    
    std::cout << "Result should be 1, it's: " << m << std::endl;
    return 0;
}

This example uses the statevector simulator, which is the default for most demonstrations.

⸻

## Simulator Implementations
	•	Matrix Product State Simulator:
Implements a basic 1D tensor network (akin to a TEBD approach) for simulating qubits on a chain. Early tests are promising, though further enhancements are planned.
	•	Clifford Gates Simulator:
Executes Clifford circuits via the stabilizer formalism. Currently, only basic functionality is verified through tests.

Both simulators may see performance improvements with future multithreading support.

⸻

## Code Structure Overview
	•	QuantumGate.h (Namespace: QC::Gates): Implements the quantum gates. Note that while the getOperatorMatrix function is retained for legacy reasons, it is now obsolete for 1-, 2-, and 3-qubit gates thanks to optimization techniques.
	•	QubitRegister.h: Manages the qubit register and includes complex operations such as partial-register measurement. The implementation of ApplyGate has evolved to remove the need for large tensor product operator matrices.
	•	QuantumAlgorithm.h: A lightweight proxy that facilitates interaction with the qubit register.
	•	Utils.h: Provides common utilities, including definitions for Bell states and measurement bases used across multiple algorithms.

For more advanced operations, refer to:
	•	NQubitsQuantumGate and NQubitsControlledQuantumGate for full matrix-based implementations.
	•	NControlledGateWithAncilla.h and NControlledNotWithAncilla.h for implementations using simpler gates combined with ancilla qubits.

To explore the algorithms in action, check out the test files in the Test directory.

⸻

## Dependencies
	•	Eigen: Utilized for efficient matrix and vector operations.
	•	FFTW: Used for verifying the Quantum Fourier Transform in simulations of the Schrödinger equation. Alternative methods for solving the equation are available within the code and may be adapted in future updates.

⸻

## Future Developments

While QCSimulator already features a broad range of quantum algorithms and simulation methods, future updates will focus on:
	•	Adding new algorithms.
	•	Enhancing existing functionalities.
	•	Optimizing performance and implementing multithreading.
	•	Addressing bug fixes as necessary.

Contributions and feedback are welcome!

Happy simulating!
