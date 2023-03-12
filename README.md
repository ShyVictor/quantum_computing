# Quantum Computing
This quantum computing project focuses on applying quantum computing techniques to artificial intelligence (AI).

This quantum computing project focuses on applying quantum computing techniques to artificial intelligence (AI). The goal of the project is to explore how quantum computing can improve the performance of machine learning algorithms and develop new quantum-based AI algorithms.

To achieve this, the project will use quantum algorithms and libraries such as Qiskit, Pennylane, and Tensorflow Quantum. These tools allow for the development of quantum machine learning models that can operate on quantum hardware, such as quantum annealers and quantum simulators.

One example of a quantum AI application is quantum clustering, which is the grouping of data into clusters. This is a fundamental task in machine learning, and quantum clustering algorithms have the potential to outperform classical algorithms in some cases.

Another application is quantum support vector machines (SVM), which is a quantum version of the classical SVM algorithm. Quantum SVMs have shown promising results in some cases and can potentially improve the performance of classical SVMs.

This project requires expertise in quantum computing, machine learning, and programming languages such as Python and QASM. The team will also need access to quantum computing hardware and simulators to test the algorithms.

Overall, this project has the potential to significantly advance the field of artificial intelligence by exploring the capabilities of quantum computing.
Theory:

![image](https://user-images.githubusercontent.com/19481699/224577761-1c02714f-883e-45bd-a185-b13d01652646.png)

Python:


```python
import pennylane as qml
from pennylane import numpy as np

dev = qml.device('default.qubit', wires=3, shots = 1000)

def epr(h,cn):
    qml.Hadamard(wires=h)
    qml.CNOT(wires=[h,cn])

def oper(h,cn):
    qml.CNOT(wires=[h,cn])
    qml.Hadamard(wires=h)


@qml.qnode(dev)
def circuit(State_Vector):
    qml.QubitStateVector(State_Vector, wires=0)
    epr(1,2)
    oper(0,1)

    fm = qml.measure(0)
    sm = qml.measure(1)

    qml.cond(sm, qml.PauliX)(wires=2)
    qml.cond(fm, qml.PauliZ)(wires=2)

    return [qml.expval(qml.PauliZ(wires=2))]

@qml.qnode(dev)
def circuit2(State_Vector):
    qml.QubitStateVector(State_Vector, wires=0)

    return [qml.expval(qml.PauliZ(wires=0))]
    
State_Vector = [1/5,2*np.sqrt(6)/5]

print(qml.draw(circuit)(State_Vector))

print(circuit(State_Vector))
print(circuit2(State_Vector))
```


QASM (Quantum Assembly) on IBM:


![image](https://user-images.githubusercontent.com/19481699/224577796-3de7dbed-65c5-45da-a9df-6d90cea2bd2b.png)

