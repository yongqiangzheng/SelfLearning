# Attention and Lexicon Regularized LSTM for Aspect-based Sentiment Analysis
注意力和词典正则化的LSTM用于方面级情感分析

## Abstract
端到端深度神经网络在训练数据少时缺乏灵活性，注意力机制可能会过度关注句子的特定部分，而忽略了为判断极性提供关键信息的位置<br>
作者提出利用词典信息这一简单有效方法，使模型灵活性和鲁棒性更强，另外，作者对注意力向量正则化，使模型获得对句子不同部分有更多的关注点

## Introduction
端到端深度学习缺乏灵活性，不能轻易地调整网络来解决一个明显的问题，比如'disappointed'（失望的）被预测为积极，'dungeon'（地牢）不能预测为消极<br>
注意力机制过度关注问题忽略关键信息，近年来，有人提出让注意力向量变得稀疏，作者认为这只能对过拟合的网络有帮助<br>
作者提出利用词典信息解决灵活性差的问题，对注意力向量正则化解决过度关注问题

## Related works

## Methodology

### Baseline AT-LSTM
作者采用Wang等人提出的AT-LSTM模型作为基线

M = tanh(\[W<sub>h</sub>H : W<sub>v</sub>v<sub>a</sub> ⊗ e<sub>N</sub>])<br>
α = softmax(w<sup>T</sup>M)<br>
r = Hα<sup>T</sup><br>
h<sup>∗</sup> = tanh(W<sub>p</sub>r + W<sub>x</sub>h<sub>N</sub>)<br>
y<sup>ˆ</sup> = softmax(W<sub>s</sub>h<sup>∗</sup> + b<sub>s</sub>)<br>
loss = -Σ<sub>i</sub> y<sub>i</sub>log(y<sup>ˆ</sup><sub>i</sub>)+λ||Θ||<sup>2</sup><sub>2</sub>

### ATLX

#### Lexicon Build
作者合并MPQA, Opinion Lexicon, Opener和Vader四个词典，SentiWordNet因引入噪音而被移除<br>
将每个词在不同词典的最大极性分数拼接，作为该词的极性分数向量

```
adorable [1.0, 1.0, 1.0, 0.55] MPQA(1.0), Opener(1.0), Opinion Lexicon(1.0) and Vader(0.55)
部分词典没有的词取所有可用词典的平均值作为缺失值
所有词典都没有的词取0向量
```

#### Lexicon Integration
L = W<sub>l</sub>V<sub>l</sub><br>
l = Lα<sup>T</sup><br>
h<sup>∗</sup> = tanh(W<sub>p</sub>r + W<sub>x</sub>h<sub>N</sub> + W<sub>l</sub>l)<br>
loss = -Σ<sub>i</sub>y<sub>i</sub>log(y<sup>ˆ</sup><sub>i</sub>)+λ||Θ||<sup>2</sup><sub>2</sub> + β · R(α)<br>
R(α) = σ(α)<br>
R(α) = =-\[-Σ<sub>i</sub><sup>N</sup> α<sub>i</sub> · log(α<sub>i</sub>)]


