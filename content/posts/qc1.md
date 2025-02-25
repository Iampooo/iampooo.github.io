---
title: '[QC] #1 Qubit, Quantum States, Phase'
description:
date: 2025-02-18T21:02:35+08:00
draft: false
tags: ["quantum",]
cover:
---
## 量子計算聽起來很厲害，但為甚麼？他比一般的電腦強在哪？

傳統電腦的基本運算單元是**位元（bit）**，一個位元不是 0 就是 1。透過許多位元的組合，電腦可以執行各種運算，例如邏輯運算或數學計算。然而，當問題變得非常複雜時——比如破解密碼、模擬化學分子或是處理大規模數據——傳統電腦可能需要花費數年甚至數十年的時間，因為它一次只能處理一個狀態。
 {{< figure src="/images/qubit.png" title="" width="400" align="center">}}
相較之下，量子計算的基本運算單元是 **量子位元（Quantum bit, Qubit）**。Qubit 的特別之處在於，它可以同時處於 0 和 1 的狀態，這種特性稱為 **疊加（superposition）**。你可以把 Qubit 想像成一枚正在被拋起的硬幣，在落下（被觀測）之前，它既不是正面也不是背面，而是同時包含這兩種可能性的狀態。這種疊加態讓量子計算機能一次探索多個解，對於某些問題（例如尋找最佳路徑或模擬量子系統），它的效率遠超傳統電腦。

## 怎麼描述 Qubit 的狀態？

既然 Qubit 介於 0 和 1 之間，我們需要一種方式來描述這種狀態。通常，Qubit 的量子態會被寫成以下形式：
$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$

這裡 $|\psi\rangle$ 是 Qubit 的量子態，$|0\rangle$ 和 $|1\rangle$ 分別代表 0 和 1 的基礎狀態，而 $\alpha$ 和 $\beta$ 是**複數（complex numbers）**，稱為機率幅度（probability amplitude）。當我們測量 Qubit 時，有 $|\alpha|^2$ 的機率得到 0，有 $|\beta|^2$ 的機率得到 1。因為機率總和必須是 1，所以： $|\alpha|^2+|\beta|^2=1$

這些 "$| \ \rangle$" 是什麼意思呢？這是量子力學中常用的 **Dirac 符號（Dirac Notation）**，用來表示量子態。實際上，這些狀態可以用矩陣（或向量）來表示：

$$|0\rangle = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \ |1\rangle = \begin{bmatrix} 0 \\ 1 \end{bmatrix} \quad |\psi\rangle = \alpha|0\rangle + \beta|1\rangle = \alpha \begin{bmatrix} 1 \\ 0 \end{bmatrix} + \beta \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \begin{bmatrix} \alpha \\ \beta \end{bmatrix}$$
這種用向量描述量子態的方式，就是量子力學的 ***第一個公設（Quantum Postulate 1）***，它告訴我們量子系統的狀態可以用數學上的向量空間來表示。這也解釋了為什麼量子計算需要用到大量的線性代數！

## 相位（Phase）：全局相位與相對相位的區別

量子計算中還有一個容易讓人困惑的概念：**相位（phase）**。包含**全局相位（global phase）** 和 **相對相位（relative phase）**：

- **全局相位（Global Phase）**
假設有兩個量子態：$| |\phi \rangle =e^{i\theta}|\psi\rangle$。這裡 $e^{i\theta}$ 是一個複數，它的 magnitude 是 1  ($|e^{i\theta}| = 1$)，只有相位角 $\theta$ 不同。這兩個狀態在物理上是一樣的，因為測量時它們的機率分布完全相同。換句話說，沒有一種測量方法可以區分這兩個狀態，所以全局相位可以忽略。

- **相對相位（Relative Phase）**
但如果相位差出現在量子態的不同部分之間，情況就完全不同了。例如，比較這兩個狀態：$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle \quad \text{和} \quad |\phi\rangle = \alpha|0\rangle + e^{i\theta}\beta|1\rangle$
雖然測量時它們得到 0 和 1 的機率一樣（還是$|\alpha|^2$ 和 $|\beta|^2$ ），但相對相位 $\theta$ 會影響量子態的行為，因此**不可以當作是同一個 state**。

這種影響在量子干涉（interference）中特別重要。例如，在量子算法中，我們可以利用相對相位讓某些結果相互增強（constructive interference）或抵消（destructive interference），這是傳統電腦無法做到的。

