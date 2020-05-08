# IBM Quantum Challenge 2020

Source code for my solutions to the [IBM Quantum Challenge](https://github.com/qiskit-community/may4_challenge_exercises).
This entry was one of the 33% of submissions that completed all exercises and placed 85th globally (top 5%).

## Exercise 1: Intro
Basic operations and Quantum Circuit manipulation using the qiskit library.

## Exercise 2: Error Mitigation
Measurement errors from energy relaxation and random sources are common in current NISQ technology. 
This excercise demonstrates the use of calibration matrices to adjust for these errors after measurement.

## Exercise 3: Quantum Cryptography
A simulation of the first proposed quantum cryptography protocol (bb84) is implemented and tested.

## Exercise 4: Circuit Decomposition
Decomposition of a Unitary matrix into a circuit of `U3` and `CX` gates within a small error margin. Additional constraints are encouraged to minimize gate usage and error propagation on NISQ systems. This solution yielded a circuit that was among the top 15% of solution to this challenge.

The Qiskit library offers a method to convert matrices to circuits and then further optimize them (transpilation). However, the transpiler performs better with simpler matrices and in particular, diagonal matrices. With this insight, the following steps were taken to optimize the circuit.

1. A hadamard transform was performed, yielding a much simpler diagonal matrix.
2. Linear and non-linear optimization models used to obtain transformations that that further reduced the matrix. These transformations correspond to basic Quantum logic gates that are currently available.
3. The simplified diagonal matrix is then passed to qiskit for transpilation, yielding the final circuit.

The iterative steps taken can be found in the Challenge 4 notebook and the models can be found in the `optimization_models.xlsx`.
