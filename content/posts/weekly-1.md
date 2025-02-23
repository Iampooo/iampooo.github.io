---
title: '紀錄一下 #1'
description: '每周紀錄一些學習和想法'
date: 2025-02-22T22:19:59+08:00
draft: false
tags: ["",]
cover:
---

**[Quandela 減少10000倍光量子計算的零件用量](https://www.quandela.com/about-us/newsroom/quandela-announces-a-100000-reduction-in-the-number-of-components-needed-for-fault-tolerant-calculations-a-major-breakthrough-for-photonic-quantum-computing/)**
- **問題是:** 光子在傳輸時會有很高的損耗，為了達到高容錯 (fault-tolerance) 的計算，單用光子會需要很大量的零件。
- **怎麼做的:** Quandela，一間歐洲量子計算公司，在[這篇論文](https://arxiv.org/pdf/2412.08611)中提出混合的方法，利用半導體量子發射器 (semiconductor quantum emitters，可高效率發射光子) 同時作為光子來源和 qubit 本身，用12個零件就可以完成一個 logical qubit
- **所以呢:** 大大增加了可擴展性和能源效率。

**[很漂亮的 ML 介紹](http://www.r2d3.us/visual-intro-to-machine-learning-part-1/) & [很漂亮的 transformer 介紹](https://bbycroft.net/llm)**
- **視覺化:** 即使是已經熟悉的內容，看到這些視覺化的介紹還是會有耳目一新的感覺

**[深度剖析LLM的背後原理 by Andrej Kaparthy](https://www.youtube.com/watch?v=7xTGNNLPyMI&t=145s)**
- **預訓練:** 用一大堆資料堆出來的是 base model ，只會文字接龍還很容易幻覺
- **解決:** 專家糾錯並提供"不會就說不會"的訓練資料，或是"不會就google"
- **短期 & 長期記憶**: context window (對話框 ) & parameters
- **左到右的線性思考**: Model needs token to think，回答落落長其實是在幫助他思考
- **模型只看的到token**: 擅長 copy paste，不擅長數數和拼字
- **現在的研究方向**: post-training RL
- **RLHF**: 創造好的答案→選出好的答案，但是會鑽漏洞
- **如何看待LLM**: 他們有時候很笨，不要完全相信，但好好利用會大大加速你的生產力
- **LLM的未來**: multimodal, agent, computer-use, computer use, test-time training
- **如何跟上**: [Chatbot Arena](https://lmarena.ai/), [AI News](https://buttondown.com/ainews), [TogetherAI](https://api.together.xyz/signin?redirectUrl=/playground/chat)
- **[Andrej Kaparthy](https://karpathy.ai/):** 他的影片都好棒

**[Productivity Rain Dance (生產力的假象)](https://www.youtube.com/watch?v=uBe2b2ayOlQ)**
- **是甚麼:** 做一些自以為對生產力有幫助的事，其實只是在裝忙，乞求可以奇蹟似的完成很多事
- **怎麼避免**: 專注在輸出而不是輸入
- **下一步:** Show my work ，因此有了紀錄一下這個系列

**[The Handoff to Bots](https://kk.org/thetechnium/)**
- **問題是**: 過去人口增長與經濟進步是高度相關的，但未來人口會下降，現在我們必須面對如何在人口萎縮的情況下維持經濟增長的問題。
- **怎麼辦**: 交棒給AI，未來的機器幫我們創造內容、提供勞動、作為主要的消費者。從「天生（Born）」轉變為「製造（Made）」的交棒。
- **人類呢**: 人類專注於無法用生產力衡量的事情：藝術、創新、探索、社交、陪伴等。

**開源 or 閉源**

關於 frontier model 開源和閉源的討論，我覺得技術本身才是重點。擁有最領先技術的不想公開，落後的就 open source 來激發創新速度，直到技術趕上成為領先者時，他們再改成閉源的模型，換原本領先的開源。

> 起司越大，洞越多；洞越多，起司越小；起司越大，起司越小。
> (on LLM's downsides)