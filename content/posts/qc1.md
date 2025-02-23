---
title: '[QC] #1 Qubit, Linear Algebra, Quantum States'
description:
date: 2025-02-18T21:02:35+08:00
draft: true
tags: ["",]
cover:
---

量子計算聽起來很厲害，但為甚麼？他比一般的電腦強在哪？

傳統電腦的基本運算單元是一個位元 (bit)，一個位元不是 0 ，就是 1。好多個位元組合起來，就可以做各種運算。

量子計算的基本運算單元是 **Quantum bit (Qubit)**，它可以同時是0和1，只是出現的機率可能不一樣，可以想成一個正在被拋起的硬幣，落下來之前 (觀測前) 不知道是正面還是背面。這個特性稱作 **superposition**，可以利用它來做傳統電腦做不到的事。

既然他介在0和1之間，要怎麼描述這種量子狀態？通常會寫成
$$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$$
"$| \ \rangle$" 是量子計算常用的符號 (Dirac Notation)，$\alpha\ \beta$ 代表有 $|\alpha|^{2}$ 的機率可以量到 0 ，$|\beta|^{2}$ 量到1

而實際上他們只是一些矩陣，因此在運算中會使用到大量的線性代數
$$|0\rangle = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \ |1\rangle = \begin{bmatrix} 0 \\ 1 \end{bmatrix} \quad |\psi\rangle = \alpha|0\rangle + \beta|1\rangle = \alpha \begin{bmatrix} 1 \\ 0 \end{bmatrix} + \beta \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \begin{bmatrix} \alpha \\ \beta \end{bmatrix}$$

## Linear Algebra
補充線性代數的基本性質和notation，之後會用到

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
| Tensor Product           | $A\otimes B = \begin{bmatrix} aB & bB \\ cB & dB \end{bmatrix}$ | 把兩個系統合併                   |
| Trace                    | $\text{Tr}(A) = \sum_i A_{ii}$                                                                                                                                         | 矩陣對角線總和，像是「總能量」或「總概率」。    |
| Rotation                 | $\exp(i\theta \vec v \cdot \vec \sigma)=\cos \theta I + i \sin \vec v \cdot \vec \sigma$                                                                               |                           |
| Diagonalizable           | $A = SDS^{-1}$ where $D$ is diagonal                                                                                                                                   | 對角化，可以拆成獨立部分處理            |
| Eigenvalue & Eigenvector | $A\|\psi\rangle = \lambda\|\psi\rangle$                                                                                                                                | 找出不變方向，像是電梯只升降不傾斜         |
| Spectral Decomposition   | $A = \sum_i \lambda_i \|\psi_i\rangle\langle\psi_i\|$                                                                                                                  | 把矩陣分解成特徵值和對應方向的總和         |
| Polar Decomposition      | $U = RP$ where $R$ is unitary, $P$ is positive                                                                                                                         | 矩陣拆成旋轉 + 變形               |
| SVD                      | $A = UDV^\dagger$                                                                                                                                                      | 矩陣分解成「基本變形」               |

