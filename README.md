# Experimenting with Trotterization on a quantum computer

Exploring Hamiltonian simulations for various Hamiltonians on a quantum computer. Different Trotterization settings and the resulting error rates are compared. All experiments are performed in Experiments.ipynb, all analysis is done in Plots.ipynb. This code was created as part of my bachelor's thesis. 

Tested on: python=3.10.13, qiskit=1.4.2, qiskit_ibm_runtime=0.37.0, numpy=2.0.1


## Summary
For a given Hamiltonian H, the time evolution of a closed system to time t is determined by the exponential exp(itH). We intend to compute the resulting state of the system via a quantum computer. In the finite dimensional case, we can decompose the Hamiltonian into a weighted sum of Pauli operators, each given by some matrix. As for non-commuting matrices we usually have exp(A+B) != exp(A)exp(B), we approximate exp(itH) by a technique known as "Trotterization", in which the problem is divided into multiple smaller steps. With more steps the approximation error decreases, but more gates are necessary to build the corresponding quantum circuit, leading to increased error rates during computation. There is thus a sweet spot for the number of Trotter steps, and we try to find this optimum for different Hamiltonians, number of qubits and optimization settings. As for commuting operators exp(A+B) = exp(A)exp(B) does hold, we limit ourselves to Hamiltonians composed of non-commuting Pauli operators.
