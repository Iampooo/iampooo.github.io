---
title: '[Qc #0] Quantum Cheatsheet'
description: Quantum Computation常用的notation和定義
date: 2025-02-23T14:07:24+08:00
draft: false
tags: ["quantum", "cheatsheet"]
cover:
math: true
---
## Linear Algebra
| Name                     | Notation                                                                                                                                                               | Meaning                   |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Ket                      | $\| \psi\rangle$                                                                                                                                                       | 行向量 (直)                   |
| Bra                      | $\langle\psi\|$                                                                                                                                                        | 列向量 (橫)                   |
| Inner Product            | $\langle\phi \| \psi \rangle$                                                                                                                                          | 內積 → 純量                   |
| Outer Product            | $\|\psi\rangle \langle \phi\|$                                                                                                                                         | 外積 → 矩陣                   |
| Complex Conjugate        | $c^*=(1+i)^*=1-i$                                                                                                                                                      | 共軛                        |
| Transpose                | $H^T$ = $\begin{bmatrix} a & b \\ c & d\end{bmatrix}^{T} = \begin{bmatrix} a & c \\ b & d\end{bmatrix}$                                                                | 轉置                        |
| Hermitian Conjugate      | $H^\dagger=(H^{*})^{T} = H$                                                                                                                                            | 共軛轉置 ($\dagger$ 叫 dagger) |
| Normal                   | $HH^\dagger=H^{\dagger}H$                                                                                                                                              | 可對角化的條件                   |
| Unitary                  | $H^\dagger H = I$                                                                                                                                                      | 保持向量長度不變                  |
| Real                     | $\langle\phi \|A \|\psi \rangle$ is real, non negative                                                                                                                 | 代表可測量的量                   |
| Positive                 | $\langle\phi \|A \|\psi \rangle \ge 0$                                                                                                                                 | 描述機率或能量                   |
| Projector                | $P=\sum\limits_{i=1}^{k}\|i\rangle \langle i\| \quad P^2=P$                                                                                                            | 選擇性保留部分空間，類似濾鏡            |
| Tensor Product           | $\|a\rangle \otimes \|b\rangle = \|a, b\rangle \quad A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \ A\otimes B = \begin{bmatrix} aB & bB \\ cB & dB \end{bmatrix}$ | 把兩個系統合併                   |
| Trace                    | $\text{Tr}(A) = \sum_i A_{ii}$                                                                                                                                         | 矩陣對角線總和，像是「總能量」或「總概率」。    |
| Rotation                 | $\exp(i\theta \vec v \cdot \vec \sigma)=\cos \theta I + i \sin \vec v \cdot \vec \sigma$                                                                               |                           |
| Diagonalizable           | $A = SDS^{-1}$ where $D$ is diagonal                                                                                                                                   | 對角化，可以拆成獨立部分處理            |
| Eigenvalue & Eigenvector | $A\|\psi\rangle = \lambda\|\psi\rangle$                                                                                                                                | 找出不變方向，像是電梯只升降不傾斜         |
| Spectral Decomposition   | $A = \sum_i \lambda_i \|\psi_i\rangle\langle\psi_i\|$                                                                                                                  | 把矩陣分解成特徵值和對應方向的總和         |
| Polar Decomposition      | $U = RP$ where $R$ is unitary, $P$ is positive                                                                                                                         | 矩陣拆成旋轉 + 變形               |
| SVD                      | $A = UDV^\dagger$                                                                                                                                                      | 矩陣分解成「基本變形」               |
## Basic Quantum
| Name                  | Notation                                                                                                                                                                      | Meaning                               |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| Density Matrix        | $\rho = \sum_i p_i \|\psi_i\rangle\langle\psi_i\|, \quad \text{Tr}(\rho) = 1$                                                                                                 | Statistical mixture of quantum states |
| POVM                  | Set $\{E_i\}$ where $E_i \geq 0, \sum_i E_i = I$                                                                                                                              | Positive Operator-Valued Measure      |
| Fidelity              | $F(\rho,\sigma) = \text{Tr}\sqrt{\sqrt{\rho}\sigma\sqrt{\rho}}$                                                                                                               | Similarity between quantum states     |
| Partial Trace         | $\text{Tr}_B(\|\alpha\rangle\langle\beta\| \otimes \|\gamma\rangle\langle\delta\|) = \|\alpha\rangle\langle\beta\| \cdot \langle\delta\|\gamma\rangle$                        | Reduced density operator              |
| Pauli Matrices        | $\sigma_x = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}, \sigma_y = \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}, \sigma_z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$ | Single-qubit basis operators          |
| CNOT Gate             | $\text{CNOT} = \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{bmatrix}$                                                                | Controlled-NOT operation              |
| Hadamard Gate         | $H = \frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}$                                                                                                         | Creates superposition                 |
| von Neumann Entropy   | $S(\rho) = -\text{Tr}(\rho\log\rho) = -\sum_i \lambda_i \log \lambda_i$                                                                                                       | Quantum information measure           |
| Schmidt Decomposition | $\|\psi\rangle_{AB} = \sum_i \sqrt{\lambda_i} \|\phi_i\rangle_A \otimes \|\varphi_i\rangle_B$                                                                                 | Bipartite state decomposition         |
| Commutator            | $[A,B] = AB - BA$                                                                                                                                                             | Measures non-commutativity            |
| Expectation Value     | $\langle A \rangle_\psi = \langle\psi\|A\|\psi\rangle$                                                                                                                        | Average measurement outcome           |
| Bell States           | $\|\Phi^+\rangle = \frac{1}{\sqrt{2}}(\|00\rangle +\|11\rangle)$                                                                                                              | Maximally entangled states            |
## Closed vs Open Quantum Systems Comparison
| Property                    | Closed Quantum System                      | Open Quantum System                                                    |
| --------------------------- | ------------------------------------------ | ---------------------------------------------------------------------- |
| **State Description**       | Pure states: \|ψ⟩                          | Mixed states: density matrix ρ                                         |
| **State Evolution**         | Unitary evolution: \|ψ(t)⟩ = U(t)\|ψ(0)⟩   | CPTP maps (completely positive trace-preserving): ρ(t) = Φ(ρ(0))       |
| **Evolution Equation**      | Schrödinger equation: iℏ∂\|ψ⟩/∂t = H\|ψ⟩   | Lindblad master equation: dρ/dt = -i[H,ρ] + ∑ᵢ γᵢ(LᵢρLᵢ† - ½{Lᵢ†Lᵢ,ρ}) |
| **Information Flow**        | Information is conserved                   | Information can leak to environment                                    |
| **Measurements**            | Projective measurements: Pₖ = \|k⟩⟨k\|     | General POVMs: Set {Eₖ} where Eₖ ≥ 0, ∑ₖEₖ = I                         |
| **Measurement Outcome**     | p(k) = \|⟨k\|ψ⟩\|²                         | p(k) = Tr(Eₖρ)                                                         |
| **Measurement for \|0⟩**    | p(0) = \|⟨0\|ψ⟩\|²                         | p(0) = Tr(\|0⟩⟨0\|ρ)                                                   |
| **Post-measurement State**  | \|ψ⟩ → \|k⟩ (collapse)                     | ρ → EₖρEₖ†/Tr(Eₖρ) (more general)                                      |
| **Reversibility**           | Reversible dynamics                        | Generally irreversible                                                 |
| **Entropy Behavior**        | Constant von Neumann entropy               | Entropy can increase (decoherence)                                     |
| **Purity**                  | Maintained: Tr(ρ²) = 1                     | Generally decreases: Tr(ρ²) ≤ 1                                        |
| **Mathematical Framework**  | Hilbert space                              | Liouville space (operators on Hilbert space)                           |
| **Common Examples**         | Idealized quantum computer, isolated atoms | Real quantum devices, NMR systems, optical cavities                    |
| **Superposition**           | Maintains coherence                        | Loses coherence over time                                              |
| **Entanglement**            | Maintained between system parts            | Can be lost to environment (decoherence)                               |
| **Time Evolution Operator** | U(t) = e^(-iHt/ℏ)                          | Φₜ(ρ) = e^(Lt)(ρ) where L is Lindbladian                               |
| **Quantum Channels**        | Identity channel                           | Depolarizing, amplitude damping, phase damping channels                |
| **Complete Description**    | Wavefunction contains all information      | Need environmental degrees of freedom for complete description         |
| **Computational Model**     | Circuit model (ideal)                      | Noise models required for accurate simulation                          |