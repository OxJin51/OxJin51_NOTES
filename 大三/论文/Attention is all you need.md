Recurrent neural networks, long short-term memory [13] and gated recurrent [7] neural networks in particular, have been firmly established as state of the art approaches in sequence modeling and transduction problems such as language modeling and machine translation [35, 2, 5]."

> Recurrent models typically factor computation along the symbol positions of the input and output sequences.

Aligning the positions to steps in computation time, they generate a sequence of hidden states $h_t$, as a function of the previous hidden state $h_{t-1}$ and the input for position t.

This inherently sequential nature precludes parallelization within training examples, which becomes critical at longer sequence lengths, as memory constraints limit batching across examples



**Recurrent Neural Networks (RNNs):** 循环神经网络。旧时代的王者，特点是按顺序处理。

**State of the Art (SOTA):** 业界最强水平。

**Parallelization (并行化):** 多任务同时开工。AI 训练速度快不快，全看能不能并行。

**Hidden State ($h_t$):** 隐藏状态。也就是模型在某一时刻的“记忆”或“理解”。