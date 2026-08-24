# 🏋️ Practice Problems

38 problems to actually cement what the notebooks taught. **None of them are solved here** - that is
the point. Each one gives you the task, a hint to unstick you, what to look up, and a concrete
"done when" so you know whether you got it right.

| Tier | Problems | You should have finished | Roughly |
|---|---|---|---|
| 🟢 **Beginner** | B1 - B10 | Problems 0 - 6 | 30-60 min each |
| 🔵 **Amateur** | A1 - A10 | Problems 5 - 11 | 1-2 hrs each |
| 🟠 **Semi-Pro** | S1 - S9 | Problems 12 - 17 | 2-4 hrs each |
| 🔴 **Pro** | P1 - P9 | All 20 | a day to a week each |

**How to use this :**
- Work in a fresh notebook. Copying cells across defeats the purpose.
- Read the hint **only after** you are properly stuck for 15 minutes.
- Every "done when" is checkable. If you cannot check it, you have not finished it.
- Several problems are deliberately **traps** - the expected answer is that something *fails*.
  Those are marked ⚠️ and they are the most valuable ones here.

---

## 🟢 Beginner

Circuits, gates, measurement and encoding. If you can do these ten, you can read almost any
introductory quantum computing paper's figures.

### B1 · Build a GHZ state
Create the 3-qubit state (|000⟩ + |111⟩)/√2 and confirm it by measurement.
- **Hint :** it is the Bell recipe with one more CNOT. H on the first qubit, then fan out.
- **Look up :** `QuantumCircuit.cx`, Problem 3
- **Done when :** you measure only `000` and `111`, each ~50%, and *never* anything else.

### B2 · Prove H is its own inverse
Show that applying H twice returns a qubit to its starting state, for a starting state that is **not** |0⟩.
- **Hint :** prepare something non-trivial first (`ry(0.7, 0)`), then compare statevectors before and after H·H.
- **Look up :** `Statevector.from_instruction`, `Statevector.equiv`
- **Done when :** the two statevectors match to numerical precision, for at least three different starting states.

### B3 · Tour the Bloch sphere
Apply RX, RY and RZ rotations of θ = π/4, π/2 and π to |0⟩ and plot each result on the Bloch sphere.
- **Hint :** RZ on |0⟩ does nothing visible. Work out why *before* you plot it.
- **Look up :** `plot_bloch_multivector`, Problem 6
- **Done when :** you can predict where the arrow will point before running the cell, and explain the RZ result in one sentence.

### B4 · All four Bell states
Build all four: |Φ+⟩, |Φ−⟩, |Ψ+⟩, |Ψ−⟩.
- **Hint :** start from the |Φ+⟩ circuit and add a single X or Z before the CNOT.
- **Look up :** Bell basis; Problem 3
- **Done when :** you have a table of the four circuits and their measured distributions, and can say which pairs are distinguishable by measurement in the computational basis alone. *(Careful - two of them are not.)*

### B5 · Measure in the X basis
Measure a qubit along X instead of Z.
- **Hint :** there is no "X measurement" instruction. Rotate the basis into Z first with an H, then measure normally.
- **Look up :** basis change, `qc.h` before `qc.measure`
- **Done when :** the |+⟩ state gives `0` 100% of the time in the X basis, while giving 50/50 in the Z basis.

### B6 · A reversible XOR
Build a circuit computing a XOR b into a third qubit, for all four classical inputs.
- **Hint :** two CNOTs, both targeting the same qubit.
- **Look up :** reversible computing, Toffoli vs CNOT
- **Done when :** you have the full 4-row truth table, verified by simulation, and can explain why the inputs must be preserved.

### B7 · How many shots do you actually need?
Measure a |+⟩ state with 10, 100, 1,000, 10,000 and 100,000 shots. Plot the deviation from 50% against shot count.
- **Hint :** plot on log-log axes and fit a slope. You are looking for −1/2.
- **Look up :** standard error of a proportion, 1/√N scaling; Problem 0
- **Done when :** your fitted slope is close to −0.5, and you can state how many shots are needed for 1% precision.

### B8 · Encode a small dataset
Angle-encode the five values [0.1, 0.3, 0.5, 0.7, 0.9] and plot all five states on Bloch spheres.
- **Hint :** `ry(2*x, 0)` - and think about why the factor of 2 is there.
- **Look up :** Problem 6
- **Done when :** the five arrows are evenly spaced, and you can say what value of x would put the state exactly at |1⟩.

### B9 · Amplitude-encode a 4-vector
Encode [0.5, 0.5, 0.5, 0.5] and then [1, 2, 3, 4] into 2 qubits.
- **Hint :** normalise first. The second vector is not a unit vector.
- **Look up :** `QuantumCircuit.initialize`, Problem 6
- **Done when :** the recovered statevector matches your hand-normalised vector, and you can state how many qubits 1,024 features would need.

### B10 · Swap without a SWAP
Exchange the states of two qubits using only CNOT gates.
- **Hint :** three of them, alternating direction.
- **Look up :** SWAP gate decomposition
- **Done when :** it works for an arbitrary input state, not just basis states. Test with `ry(0.6)` on one qubit and `rx(1.1)` on the other.

---

## 🔵 Amateur

Real algorithms and your first working quantum ML models.

### A1 · Deutsch-Jozsa
Determine whether a black-box function is constant or balanced in **one** query.
- **Hint :** put the input register in uniform superposition, apply the oracle, then H everything and measure. All-zeros means constant.
- **Look up :** Deutsch-Jozsa algorithm; phase kickback
- **Done when :** it works for at least 3 different oracles on 3 qubits, and you can state how many queries a classical algorithm would need in the worst case.

### A2 · Bernstein-Vazirani
Recover a hidden bitstring s from an oracle computing s·x mod 2, in one query.
- **Hint :** structurally almost identical to A1. The measured bitstring *is* the answer.
- **Look up :** Bernstein-Vazirani algorithm
- **Done when :** you recover a 5-bit secret in a single circuit execution, and can explain why classical needs 5 queries.

### A3 · Map the SWAP test
Sweep the angle difference between two angle-encoded states from 0 to π and plot measured fidelity against the analytic cos²(Δ) curve.
- **Hint :** use enough shots that the error bars are smaller than the features you are looking at. Problem 7 explains the 1/√shots noise.
- **Look up :** Problem 7
- **Done when :** your points sit on the analytic curve within shot noise, and you can state the fidelity of two orthogonal states.

### A4 · Build a fidelity kernel from scratch ⭐
Implement a quantum kernel yourself using the embed/adjoint trick, and check it against `FidelityQuantumKernel`.
- **Hint :** encode x, apply the inverse encoding of x′, read the probability of the all-zeros bitstring.
- **Look up :** Problem 9.2, `qml.adjoint`, `QuantumCircuit.inverse`
- **Done when :** your kernel matrix matches Qiskit's to ~1e-6, is symmetric, and has 1s on the diagonal.

### A5 · QSVM on a new dataset
Run the Problem 9 pipeline on `load_wine` (13 features, 3 classes).
- **Hint :** 13 features means 13 qubits. You will have to reduce first - and that decision is part of the problem.
- **Look up :** Problems 9.1, 18
- **Done when :** you report quantum accuracy, a tuned classical baseline **on the same reduced features**, and both runtimes.

### A6 · Teleport an arbitrary state
Extend Problem 4 to teleport a state you choose, and *prove* it arrived.
- **Hint :** the proof is the inverse-preparation trick - apply U† to the receiving qubit and check you always measure 0.
- **Look up :** Problem 4
- **Done when :** three different input states each teleport with 100% verified success.

### A7 · Superdense coding
Send 2 classical bits by physically transmitting 1 qubit.
- **Hint :** it is teleportation's mirror image. Share a Bell pair first; the sender's local I/X/Z/XZ picks which Bell state the receiver decodes.
- **Look up :** superdense coding
- **Done when :** all four 2-bit messages decode with 100% accuracy.

### A8 · A VQC for XOR
Train a variational classifier on the 4-point XOR/parity problem.
- **Hint :** XOR is the classic non-linearly-separable case. If your circuit cannot do it, the feature map is the suspect - not the optimizer.
- **Look up :** Problems 10, 13
- **Done when :** 100% on all four points, and you can state the minimum number of layers that worked.

### A9 · Three-class classification
Extend the Problem 11 VQC to all 3 classes of Iris.
- **Hint :** one output value cannot encode three classes. Use `SamplerQNN` and read a probability distribution, or measure several observables.
- **Look up :** `SamplerQNN`, `VQC`, one-hot encoding; Problem 11
- **Done when :** you produce a 3x3 confusion matrix and beat a majority-class baseline convincingly.

### A10 · Cross-framework check ⚠️
Implement the *same* model in both Qiskit and PennyLane and compare.
- **Hint :** identical feature map, identical ansatz, identical data, identical seed. The results still will not match exactly - work out which of gate ordering, parameter convention or optimizer is responsible.
- **Look up :** Problems 10, 11
- **Done when :** the two accuracies agree within a few percent **and** you can name the specific source of the remaining difference.

---

## 🟠 Semi-Pro

Failure modes, noise, and algorithm design. This is where you stop following recipes.

### S1 · Global vs local cost functions ⚠️
Repeat the Problem 12 barren plateau experiment with a **global** cost (Z on every qubit) and a **local** one (Z₀Z₁). Plot both.
- **Hint :** the global cost should plateau at much shallower depth. Sweep depth, not just qubit count.
- **Look up :** Cerezo et al., "Cost function dependent barren plateaus"; Problem 12
- **Done when :** you have two curves on one log plot and can state the practical rule they imply.

### S2 · Layer-by-layer training
Train a deep VQC one layer at a time, freezing each as you go, and compare against training everything at once.
- **Hint :** initialise each new layer near the identity so adding it does not disturb what you already learned.
- **Look up :** layerwise learning; Skolik et al. 2021
- **Done when :** you plot both training curves and report whether layerwise actually helped at this scale. *(A negative result is a valid answer if you show it honestly.)*

### S3 · Fourier spectrum of an encoding ⭐
Show empirically that a data-re-uploading circuit's output is a truncated Fourier series, and that adding uploads adds frequencies.
- **Hint :** fix the weights, sweep a single input x over [0, 2π], record the output, and FFT it.
- **Look up :** Schuld, Sweke & Meyer, "The effect of data encoding on the expressive power of variational quantum machine learning models"; Problem 13
- **Done when :** you show that L uploads give you frequencies up to L, with a plot of the spectrum for L = 1, 2, 3.

### S4 · Better readout mitigation ⚠️
Replace the matrix inverse in Problem 14 with a constrained least-squares fit that forces probabilities to be non-negative and sum to 1.
- **Hint :** `scipy.optimize.nnls`, or `minimize` with constraints. First, deliberately construct a case where the plain inverse returns a negative probability.
- **Look up :** M3 mitigation, `mthree`; Problem 14
- **Done when :** you show a concrete case where the inverse gives a negative probability and your version does not.

### S5 · Extrapolation shoot-out
Compare linear, polynomial, exponential and Richardson extrapolation for ZNE on the same data.
- **Hint :** with k noise scale factors you can fit a degree-(k−1) polynomial exactly - which is not the same as fitting it *well*. Watch what high-degree fits do.
- **Look up :** Richardson extrapolation, `mitiq`; Problem 14
- **Done when :** you rank all four by error against the exact answer and explain why the winner won, in terms of the noise channel.

### S6 · VQE for a bigger molecule
Run VQE on LiH or H₃⁺ with a UCCSD ansatz.
- **Hint :** `qml.qchem.excitations` generates the excitation lists for you. Expect a large jump in parameter count and runtime - measure both.
- **Look up :** `qml.UCCSD`, `qml.qchem.molecular_hamiltonian`; Problem 15
- **Done when :** you reach chemical accuracy (1.6 mHa) against exact diagonalisation, and report parameter count and wall-clock time versus H₂.

### S7 · QAOA with a constraint
Solve **weighted** MaxCut, then a problem needing exactly k selected items using the XY mixer.
- **Hint :** the XY mixer preserves Hamming weight, so your initial state must already have the right number of 1s.
- **Look up :** `qml.qaoa.xy_mixer`, constrained QAOA; Problem 16
- **Done when :** every sampled bitstring satisfies the constraint by construction, not by filtering afterwards.

### S8 · Grover without knowing M
Find a marked item when you do **not** know how many solutions exist.
- **Hint :** two routes - quantum counting via phase estimation, or exponential search trying k = 1, 2, 4, 8, …
- **Look up :** quantum counting, BBHT algorithm; Problem 17
- **Done when :** it succeeds for M = 1, 2 and 4 marked items without being told M, and you report the average query count.

### S9 · Train under noise ⚠️
Train the Problem 10 VQC with the Problem 14 noise model active during training.
- **Hint :** parameter-shift gradients get very noisy. Consider a gradient-free optimizer, and expect to need far more shots.
- **Look up :** noise-aware training, SPSA optimizer
- **Done when :** you report accuracy vs 2-qubit gate error rate for at least 4 error rates, and identify where training stops working entirely.

---

## 🔴 Pro

Research-grade. Several of these are open enough that a good writeup would be worth sharing.

### P1 · Encoding expressivity study ⭐
Systematically characterise which functions different feature maps can express, using Fourier analysis.
- **Hint :** build on S3. Compare angle encoding, ZZ maps, and re-uploading at matched parameter counts - matched parameters is what makes it a fair comparison.
- **Look up :** Schuld, Sweke & Meyer 2021; Problem 13
- **Done when :** you produce a table of accessible frequency spectra per encoding and can predict, in advance, which datasets each will fail on.

### P2 · Geometric difference across many datasets
Compute the Huang et al. geometric difference for 10+ datasets and test how well it predicts actual quantum-vs-classical performance.
- **Hint :** regularisation sensitivity is the whole game - always report the sweep. Problem 20 shows the ordering flipping at small reg.
- **Look up :** Huang et al., "Power of data in quantum machine learning"; Problem 20
- **Done when :** you have a scatter plot of g against measured accuracy gap, with a correlation coefficient and an honest discussion of the outliers.

### P3 · Trainable quantum kernels
Rather than fixing the feature map, **train** its parameters to maximise centered kernel-target alignment.
- **Hint :** KTA is differentiable. Optimise it directly, then train the SVM on the resulting kernel.
- **Look up :** Hubregtsen et al., "Training quantum embedding kernels"; `qml.kernels.target_alignment`; Problem 20
- **Done when :** the trained kernel beats every fixed feature map you tried, on a dataset where the fixed ones were mediocre.

### P4 · Quantum autoencoder
Compress an n-qubit state into fewer qubits and reconstruct it.
- **Hint :** train so the discarded "trash" qubits end up in |0⟩. Fidelity of the trash register is your loss.
- **Look up :** Romero et al., "Quantum autoencoders for efficient compression of quantum data"
- **Done when :** you achieve >95% reconstruction fidelity on a structured family of states, and show it fails on random states - which is the correct behaviour.

### P5 · Dequantise your own model ⚠️
Take a quantum model that works and try to **match it classically** with random Fourier features or a classical shadow.
- **Hint :** this is the experiment most likely to produce an uncomfortable result. Do it anyway. If a classical surrogate matches your quantum model, that is a finding worth publishing, not hiding.
- **Look up :** Tang's dequantisation results; random Fourier features; classical shadows
- **Done when :** you report the classical surrogate's accuracy and cost alongside the quantum model's, and state plainly whether the advantage survived.

### P6 · Run it on real hardware
Take any notebook from this repo end to end on an actual QPU.
- **Hint :** start with Problem 3, a Bell state - two gates. Compare the counts to your simulator run, then apply Problem 14's readout mitigation.
- **Look up :** IBM Quantum Platform, `qiskit-ibm-runtime`, PennyLane plugins; Problem 14
- **Done when :** you have ideal, raw-hardware and mitigated results side by side, plus a note on how long the queue took.

### P7 · Classify a phase of matter
Use `phase_of_matter_data` (or generate your own transverse-field Ising ground states) and classify the phase.
- **Hint :** this is genuinely quantum data, so there is no encoding step - a major advantage. Locate the critical point from your classifier's uncertainty.
- **Look up :** `qiskit_machine_learning.datasets.phase_of_matter`; Carrasquilla & Melko, "Machine learning phases of matter"; Problem 19
- **Done when :** you identify the phase transition point to within a few percent of the known value.

### P8 · Measurement budget optimisation
For a VQE Hamiltonian, minimise the total shots needed for a target energy precision by grouping commuting Pauli terms.
- **Hint :** qubit-wise commuting terms share a measurement basis. This is a graph colouring problem.
- **Look up :** Pauli grouping, `qiskit.quantum_info.PauliList.group_commuting`, shot allocation strategies; Problem 15
- **Done when :** you hit chemical accuracy on H₂ with measurably fewer total shots than naive term-by-term measurement, with the factor reported.

### P9 · Barren plateau mitigation bake-off
Implement and compare at least four strategies: identity-block initialisation, layerwise training, local cost functions and a problem-inspired ansatz.
- **Hint :** hold everything else fixed - same qubits, same depth, same optimizer - or the comparison means nothing.
- **Look up :** Grant et al. (identity block init); Cerezo et al. (local costs); Problem 12
- **Done when :** you have gradient-variance-vs-qubits curves for all four on one plot, with a recommendation and its caveats.

---

## 📌 Where to get unstuck

- **The notebooks themselves.** Every problem above names the ones it builds on.
- [Qiskit documentation](https://quantum.cloud.ibm.com/docs) · [PennyLane demos](https://pennylane.ai/qml/demonstrations/) - the demos are excellent and cover several problems here directly.
- [Quantum Computing Stack Exchange](https://quantumcomputing.stackexchange.com/)
- The lecture PDFs in [`materials/`](materials/), with video links in [`materials/README.md`](materials/README.md).

**If you get a strange result, suspect your setup before you suspect physics.** In roughly this
order : shot noise, an unfixed random seed, qubit ordering conventions (Qiskit prints the most
significant qubit first), a transpiler optimisation that cancelled the gates you cared about, and
data that was never scaled properly.

**Solved something interesting?** Open a PR. Good solutions to the Pro problems would make excellent
additions to this repo. 🤝
