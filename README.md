# QuantumAI-Noob2Pro
Building an OpenSource repo for guiding NOOBS --to-> PRO in QuantumAI 🚀

🤝 Feel free to contribute and help serve the community ! 🌎

---
### 👨‍💻 Pre-requisites : 
- Intermediate Machine Learning and Deep Learning Knowledge.
- Basic idea about Quantum Mechanics

---
### 🛠️ Setup

```bash
python -m venv .quantumvenv
source .quantumvenv/bin/activate      # Windows: .quantumvenv\Scripts\activate
pip install -r requirements.txt
```

Every notebook in this repo runs end to end on a laptop - no quantum hardware needed.

---

### How to proceed with this repository ? 🤔

🏋️ **Want to practise?** [PRACTICE.md](PRACTICE.md) has **38 unsolved problems** across four tiers - Beginner, Amateur, Semi-Pro and Pro - each with a hint, references, and a checkable "done when".

🗺️ **New here? Start with the [ROADMAP](ROADMAP.md)** - it explains the order the problems are meant to be read in, roughly how long each stage takes, and the question each stage is answering.

➡️ **Read the `0-ReadFIRST.ipynb` to understand the required terminolgies that you will be encountering in the listed problems.**

- **Problem 1 :** Flip a single bit (0 to 1 or 1 to 0) using a quantum gate

- **Problem 2 :** Creating superposition using the Hadamard (H) Gate

- **Problem 3 :** Create an entangled Bell State using CNOT Gate

- **Problem 4 :** Quantum Teleportation - Transfer the state of one qubit to another, using entanglement and classical communication.

- **Problem 5 :** Quantum State Classification - Introduces the idea of classifying quantum states based on measurement outcomes.

- **Problem 6 :** Quantum Feature Encoding - The task is to encode classical data (e.g., a numerical feature) into a quantum state.

- **Problem 7 :** Quantum Nearest Neighbour(QNN) - Compare quantum states and classify a new data point based on its similarity to a set of labeled quantum states.

- **Problem 8 :** Quantum Principal Component Analysis (QPCA) - Task is to find the principal components of a dataset encoded as quantum states.

- **Problem 8.1 :** Quantum Principal Component Analysis (QPCA) Application on a generated dataset - Apply QPCA techniques on a small generated dataset.

- **Problem 9 :** Quantum Support Vector Machine (QSVM) - Using QSVM determine the accuracy of a basic generated dataset.

- **Problem 9.1 :** Quantum Support Vector Machine (QSVM) - Application of QSVM on Iris Dataset

- **Problem 9.2 :** Quantum Support Vector Machine (QSVM) - Application of QSVM with PennyLane, and what actually makes something a kernel.

- **Problem 10 :** Variational Quantum Classifier (VQC) - The first model here that genuinely *trains*. The hybrid quantum-classical loop and the parameter-shift rule.

- **Problem 11 :** Quantum Neural Networks in Qiskit - The same model built with `EstimatorQNN` and `VQC`, trained with a gradient-free optimizer.

- **Problem 12 :** Barren Plateaus - Measure for yourself why gradients vanish exponentially with qubit count, and why bigger quantum models are *worse*.

- **Problem 13 :** Data Re-uploading Classifier - The fix. A **single qubit** beats the two-qubit model of Problem 10.

- **Problem 14 :** Noise and Error Mitigation - Realistic noise models, readout error mitigation with a calibration matrix, and zero-noise extrapolation.

- **Problem 15 :** Variational Quantum Eigensolver (VQE) - Compute the ground state energy and full dissociation curve of the H₂ molecule.

- **Problem 16 :** QAOA - Solve MaxCut, and see how combinatorial optimization becomes a ground-state problem.

- **Problem 17 :** Grover's Algorithm - A *provable* O(√N) speedup, and the amplitude amplification primitive behind most QML speedup claims.

---

##### 🌍 Real-world problems - does any of this actually work ?

- **Problem 18 :** Real data, head to head - Breast cancer diagnosis with tuned classical ML vs a tuned quantum kernel, scored on accuracy *and* wall-clock time. **Classical wins**, and the best quantum kernel turns out to be the one with no entanglement.

- **Problem 19 :** Where quantum actually wins - On quantum-generated data the quantum kernel hits **100%** while five tuned classical models top out at 80%, and the gap *widens* with qubit count.

- **Problem 20 :** Should you use quantum ML? - A validated decision procedure: centered kernel-target alignment, geometric difference, learning curves and a hardware cost estimate. Tested against the known answers from Problems 18 and 19.


< List will be updated as added >

---

### What to read/ study for this ? 🤓
#### Foundational Papers to Study : 📑
1. [The Road to Quantum Artificial Intelligence](https://arxiv.org/ftp/arxiv/papers/0705/0705.3360.pdf)
2. [Quantum Neuron: an elementary building block for machine learning on quantum computers](https://arxiv.org/pdf/1711.11240)
3. [Quantum algorithms for supervised and unsupervised machine learning](https://arxiv.org/pdf/1307.0411)
4. [Quantum Artificial Intelligence: A Brief Survey](https://arxiv.org/pdf/2408.10726)

#### Papers behind Problems 10 - 20 : 📄
5. [Barren plateaus in quantum neural network training landscapes](https://www.nature.com/articles/s41467-018-07090-6) - *Problem 12*
6. [Data re-uploading for a universal quantum classifier](https://quantum-journal.org/papers/q-2020-02-06-226/) - *Problem 13*
7. [A variational eigenvalue solver on a photonic quantum processor](https://www.nature.com/articles/ncomms5213) - *Problem 15*
8. [A Quantum Approximate Optimization Algorithm](https://arxiv.org/abs/1411.4028) - *Problem 16*
9. [A fast quantum mechanical algorithm for database search](https://arxiv.org/abs/quant-ph/9605043) - *Problem 17*
10. [Supervised learning with quantum-enhanced feature spaces](https://www.nature.com/articles/s41586-019-0980-3) - *Problem 19*
11. [Power of data in quantum machine learning](https://www.nature.com/articles/s41467-021-22539-9) - *Problem 20*

#### Books and Materials : 📚
1. Quantum Machine Learning Book by S Pattanayak - Get this book from this repo.
2. Overall Summarised Concepts - https://blog.paperspace.com/beginners-guide-to-quantum-machine-learning/
3. Lecture Material PDF resources to learn  https://github.com/Qiskit/platypus/tree/main/notebooks/summer-school/2021/resources

#### Video Resources : 🎥
1. Understand the DIRAC NOTATIONS and the basic representations here - https://youtu.be/MrLf6m_AFc0?si=Cjjj40mY11QCPNOd&t=101
2. Introduction to Quantum Computing by Qiskit - https://www.youtube.com/playlist?list=PLOFEBzvs-VvrXTMy5Y2IqmSaUjfnhvBHR
3. Quantum Machine Learning by Peter Wittek - https://www.youtube.com/playlist?list=PLmRxgFnCIhaMgvot-Xuym_hn69lmzIokg
4. Quantum Machine Learning by Seth Lloyd (MIT) - https://www.youtube.com/watch?v=Lbndu5EIWvI

#### TOP OVERALL RESOURCES : 🥇
1. https://quantummlhandbook.vercel.app/docs/get-started
2. https://github.com/krishnakumarsekar/awesome-quantum-machine-learning
3. https://qiskit-community.github.io/qiskit-machine-learning/tutorials/index.html

---
#### Connect with me on Linkedin - [@shreyanbasuray](https://www.linkedin.com/in/shreyanbasuray) 🪩 

─── ⋆⋅☆⋅⋆ ───
