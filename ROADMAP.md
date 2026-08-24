# 🗺️ The Noob ➡️ Pro Roadmap

A guided path through this repository. The problems are **ordered on purpose** - each one sets up a
question that the next one answers. If you only read the notebooks you like the sound of, you will
miss the argument they are making together.

> **How to use this page :** find the stage that matches where you are, do the notebooks in order,
> and do not skip the `#### TASK :` sections at the bottom of each one. That is where the learning
> actually happens.
>
> When you want to test yourself away from the notebooks, [PRACTICE.md](PRACTICE.md) has 38 unsolved
> problems tiered Beginner → Pro, cross-referenced to the stages below.

---

## ⏱️ Time estimates

| Stage | Notebooks | Time | You will be able to... |
|---|---|---|---|
| 0. Foundations | `0` | 1-2 hrs | read a quantum circuit without panicking |
| 1. Quantum Computing Basics | `1` - `4` | 4-6 hrs | build, simulate and reason about small circuits |
| 2. Encoding & Similarity | `5` - `7` | 4-6 hrs | get classical data *into* a quantum computer |
| 3. Classical Algorithms, Quantum Kernels | `8` - `9.2` | 6-8 hrs | build a working quantum classifier |
| 4. Trainable Quantum Models | `10` - `13` | 8-10 hrs | train variational circuits, and know why they fail |
| 5. Reality Check | `14` | 3-4 hrs | run on noisy hardware and mitigate the damage |
| 6. Beyond Classification | `15` - `17` | 6-8 hrs | chemistry, optimization, and provable speedups |
| 7. Real-World Problems | `18` - `20` | 6-8 hrs | judge, honestly, whether quantum helps on *your* data |

Roughly **36-55 hours** end to end at a comfortable pace.

---

## 👨‍💻 Before you start

**You need :**
- Python, NumPy and scikit-learn at a working level
- Intermediate machine learning - you should know what a kernel, a loss function and SGD are
- Linear algebra : vectors, matrices, eigenvalues, complex numbers
- A rough idea of what a quantum state is (the video links in the README cover this)

**You do NOT need :**
- A physics degree
- Access to real quantum hardware - everything here runs on a simulator on your laptop

**Setup :**
```bash
python -m venv .quantumvenv
source .quantumvenv/bin/activate      # Windows: .quantumvenv\Scripts\activate
pip install -r requirements.txt
```

---

## Stage 0 · Foundations

### 📓 `0-ReadFIRST.ipynb`
The vocabulary. Simulators, statevectors, measurement, transpilation, shots, and the two gates that
matter most (H and CNOT).

> **Read this first, properly.** Every later notebook assumes it.

---

## Stage 1 · Quantum Computing Basics
*The question : what can a quantum circuit actually do?*

| Notebook | Concept | The idea to take away |
|---|---|---|
| `1-Problem1` | The X gate | A qubit can do everything a classical bit can |
| `2-Problem2` | The Hadamard gate | ...and it can also be in **superposition** |
| `3-Problem3` | Bell states | Two qubits can be **entangled** - correlated beyond anything classical |
| `4-Problem4` | Quantum teleportation | Entanglement + 2 classical bits moves a quantum state |

**Checkpoint - can you answer these?**
- Why does applying H twice return you to the original state?
- Why can't you measure a qubit twice and get more information the second time?
- In teleportation, why is X conditioned on one measured bit and Z on the other?

---

## Stage 2 · Getting Data Into a Quantum Computer
*The question : classical data is numbers. Quantum computers hold states. How do you bridge that?*

| Notebook | Concept | The idea to take away |
|---|---|---|
| `5-Problem5` | Measurement as classification | Measurement statistics *are* your model output |
| `6-Problem6` | Angle & amplitude encoding | **Encoding is a modelling decision**, not a formality |
| `7-Problem7` | SWAP test, quantum nearest neighbour | You can measure the similarity of two states directly |

**Checkpoint :**
- Amplitude encoding fits n features into log₂(n) qubits. Why isn't that a free lunch?
- The SWAP test gives |⟨a\|b⟩|². What information about the overlap is lost, and does it matter?
- Problem 7 finds a **tie**. Why is comparing two noisy estimates without a tolerance a bug?

---

## Stage 3 · Quantum Kernels
*The question : can we get an actual machine learning model out of this?*

| Notebook | Concept | The idea to take away |
|---|---|---|
| `8-Problem8` | QPCA on toy data | Density matrices, eigenvalues as explained variance |
| `8.1-Problem8.1` | QPCA on generated data | The same machinery on a real-ish dataset |
| `9-Problem9` | QSVM with `ZZFeatureMap` | A quantum kernel plugs straight into scikit-learn |
| `9.1-Problem9.1` | QSVM on Iris | It scales to a real, multi-class dataset |
| `9.2-Problem9.2` | QSVM in PennyLane | **What makes something a kernel**, and the classical baseline |

**Checkpoint :**
- Why is `k(x, x') = f(x) · f(x')` not a valid kernel?
- The quantum kernel ties with an RBF kernel on circles. Is that a failure? *(No - and you should be able to say why.)*
- What does `SVC(kernel='precomputed')` actually receive?

---

## Stage 4 · Trainable Quantum Models 🔥
*The question : so far the quantum part has been fixed. What if we **train** the circuit?*

**This is the heart of the repository.** These four notebooks form a single argument - do them in
order and do not skip 12.

| Notebook | Concept | The idea to take away |
|---|---|---|
| `10-Problem10` | Variational Quantum Classifier | The hybrid loop; parameter-shift gradients. **Plateaus at ~85%** |
| `11-Problem11` | Qiskit `EstimatorQNN` & `VQC` | A different framework and optimizer hit **the same 85%** - so it's the model |
| `12-Problem12` | **Barren plateaus** | Gradients vanish exponentially with qubit count. **Bigger is worse** |
| `13-Problem13` | Data re-uploading | Better *structure* fixes it - **one qubit reaches 97%** |

**The argument in one line :** in quantum machine learning, *how you encode the data is the model*.
Ansatz design and qubit count are secondary.

**Checkpoint :**
- Why can't you backpropagate through a quantum circuit?
- Why does a *flat* loss landscape kill training even though the gradient is unbiased?
- Problem 10 initialises weights with σ = 0.1 and Problem 13 with σ = 1.0. Why is that not a contradiction?

---

## Stage 5 · Reality Check
*The question : none of the above has touched a real, noisy device. How much of it survives?*

| Notebook | Concept | The idea to take away |
|---|---|---|
| `14-Problem14` | Noise models, readout mitigation, ZNE | Mitigation buys accuracy with **runtime**, and it is not error correction |

**Checkpoint :**
- Which is worse on today's hardware, a 1-qubit gate or a 2-qubit gate - and by how much?
- Why must folded circuits be transpiled with `optimization_level=0`?
- Why does an *exponential* extrapolation beat a linear one for depolarizing noise?

---

## Stage 6 · Beyond Classification
*The question : classification is not the only thing quantum computers are good for. What else?*

| Notebook | Concept | The idea to take away |
|---|---|---|
| `15-Problem15` | VQE on H₂ | Same hybrid loop, energy as the loss. **Chemistry is the killer app** |
| `16-Problem16` | QAOA on MaxCut | Any 0/1 assignment problem is a ground-state problem |
| `17-Problem17` | Grover & amplitude amplification | A **provable** O(√N) speedup - and what it costs |

**Checkpoint :**
- Why does the variational principle mean lower energy is *always* better?
- What is a "problem-inspired ansatz", and how does it dodge barren plateaus?
- Grover is a rotation. What happens if you run too many iterations?

---

## Stage 7 · Real-World Problems, and the Honest Verdict 🌍
*The question : forget the toys. On a real problem, does any of this actually beat scikit-learn?*

**This is the stage that turns you from someone who can run a quantum classifier into someone who
can tell whether the result means anything.** Do all three, in order - 18 and 19 reach opposite
conclusions on purpose, and 20 is what resolves them.

| Notebook | Concept | The idea to take away |
|---|---|---|
| `18-Problem18` | Breast cancer: classical vs quantum | **Classical wins** - ~96% in 1 ms vs ~95% in 12 s. The best quantum kernel has *zero* entangling gates |
| `19-Problem19` | Quantum-native data | **Quantum wins** - 100% vs 80% for five tuned classical models, and the gap grows with qubit count |
| `20-Problem20` | Should you use quantum ML? | A decision procedure - alignment, geometric difference, learning curves, hardware cost - **validated against 18 and 19** |

**The resolution :** quantum models win on **quantum-structured data** and lose on
classically-structured data. That is a sharp, predictive rule, and Problem 20 turns it into
something you can measure on a dataset you have never seen before.

**Checkpoint :**
- Why did PCA have to run *before* the quantum model in Problem 18 - and what did that cost?
- Why is a `z_feature_map` kernel with no entanglement barely "quantum" at all?
- Problem 19's quantum kernel matched the feature map that generated the data. Why does that make
  the win real but narrow?
- Why must you **center** a kernel before computing target alignment? *(In Problem 20 the uncentered
  version gets the answer backwards.)*
- Why is a large geometric difference **necessary but not sufficient** for quantum advantage?

---

## 🧭 Three threads running through the whole repo

Once you have finished, these are the three things worth remembering.

**1. Encoding is everything.** Problems 6, 9.2, 10 and 13 are all, ultimately, about the feature
map. It sets what your model can express; nothing downstream can add what the encoding left out.

**2. Structure beats scale.** Classical deep learning rewards size. Quantum models punish it
(Problem 12). Every technique that works - re-uploading, UCCSD, the QAOA ansatz - works because it
builds in structure you already knew about.

**3. Always run the classical baseline.** Problem 9.2 makes this explicit, Problems 18-20 make it
the whole point, and it applies everywhere. "96% accuracy" means nothing without "and scikit-learn
gets 96% in 40 milliseconds".

**A fourth, earned by the end :** most honest results in this field are negative, and the negative
results are the map. Problem 18 tells you where not to look. Problem 19 tells you where to look.
Problem 12 tells you which failure mode to design around. Knowing the difference between a genuine
advantage and a rigged demo is the actual pro skill.

---

## 🚀 Where to go next

Once you have finished this repo, these are the natural next steps :

**Deepen the theory**
- Nielsen & Chuang, *Quantum Computation and Quantum Information* - still the standard text
- Schuld & Petruccione, *Machine Learning with Quantum Computers* - the QML book
- The lecture PDFs in [`materials/`](materials/) - Qiskit Summer School, with video links in [`materials/README.md`](materials/README.md)

**Topics this repo doesn't cover yet**
- Quantum error correction (surface codes, stabilisers) - `materials/5` is the lecture
- Shor's algorithm, QFT and phase estimation - `materials/3` and `materials/4`
- Quantum GANs and quantum generative models
- Quantum reinforcement learning
- Tensor-network methods and classical simulation of quantum ML
- Fault-tolerant algorithms : HHL, quantum linear algebra, and why the fine print matters

**Run on real hardware**
- [IBM Quantum Platform](https://quantum.ibm.com/) - free access to real devices
- [PennyLane plugins](https://pennylane.ai/plugins/) - AWS Braket, IonQ, Rigetti and more
- Start with Problem 3 (a Bell state) and compare the counts to your simulator run. Then re-read
  Problem 14.

**Practise**
[PRACTICE.md](PRACTICE.md) - 38 unsolved problems, Beginner through Pro. Several of the Pro ones are
open enough that a good writeup would be worth sharing.

**Contribute**
New problems, fixes and better explanations are all welcome - open a PR. 🤝
