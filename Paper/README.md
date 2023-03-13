# Quick Reading 
```
##

> 
---

### Motivation

### Model

### Result

---
```



## BiSyn-GAT+: Bi-Syntax Aware Graph Attention Network for Aspect-based Sentiment Analysis

> 2022 ACL(Findings) [(Paper)](/Paper/pdf/2022_ACL(Findings)_BiSyn-GAT%2B%20Bi-Syntax%20Aware%20Graph%20Attention%20Network%20for%20Aspect-based%20Sentiment%20Analysis.pdf)
---
### Motivation
1. 位置和依存树都不一定能将方面及其对应上下文对齐 **(intra-aspect)**
2. 无法对多个方面的复杂关系建模 **(inter-aspect)**

### Model
1. 成分树将复杂句子划分成多个子句，对齐方面及其上下文
2. 利用依存树的句法信息和成分树的层次结构，对方面上下文和方面之间的关系进行建模

<center>
<img src='/Paper/figure/BiSyn-GAT2.png' width='50%' height='50%' />
Figure 1
</center>

![Model](/Paper/figure/BiSyn-GAT2.png)

### Result
![Result](/Paper/figure/BiSyn-GAT3.png)

---
## Attention and Lexicon Regularized LSTM for Aspect-based Sentiment Analysis

> 2019 ACL [(Paper)](/Paper/pdf/2019_ACL_Attention%20and%20Lexicon%20Regularized%20LSTM%20for%20Aspect-based%20Sentiment%20Analysis.pdf)
---

### Motivation
1. 端到端深度神经网络在训练数据少时缺乏灵活性，注意力机制可能会过度关注句子的特定部分，而忽略了为判断极性提供关键信息的位置 **(over-attention)**
2. 作者提出利用词典信息这一简单有效方法，使模型灵活性和鲁棒性更强，另外，作者对注意力向量正则化，使模型获得对句子不同部分有更多的关注点 **(lexicon+regularize)**
### Model

![Model](/Paper//figure/ATLX2.png)
### Result

---


## 

> 2019 ACL [(Paper)](/Paper/pdf/2019_ACL_Attention%20and%20Lexicon%20Regularized%20LSTM%20for%20Aspect-based%20Sentiment%20Analysis.pdf)

### Motivation
端到端深度神经网络在训练数据少时缺乏灵活性，注意力机制可能会过度关注句子的特定部分，而忽略了为判断极性提供关键信息的位置 **(over-attention)**

作者提出利用词典信息这一简单有效方法，使模型灵活性和鲁棒性更强，另外，作者对注意力向量正则化，使模型获得对句子不同部分有更多的关注点 **(lexicon+regularize)**

### Method

Lexicon Build

作者合并MPQA, Opinion Lexicon, Opener和Vader四个词典，SentiWordNet因引入噪音而被移除。将每个词在不同词典的最大极性分数拼接，作为该词的极性分数向量

adorable [1.0, 1.0, 1.0, 0.55] MPQA(1.0), Opener(1.0), Opinion Lexicon(1.0) and Vader(0.55)

部分词典没有的词取所有可用词典的平均值作为缺失值,所有词典都没有的词取0向量

#### Attention Regularization
由于注意力过拟合，模型更注意句子后面的部分，作者在损失函数加入对注意力分数的正则化R(α)，提出了两种计算方法：标准差和负信息熵
### Conclusion
1. 作者提出利用词典信息搭建神经网络，同时使用2种正则化方法减少注意力过拟合问题的影响，特定于域和方面的细粒度词典可以进一步改善类似模型

2. 负信息熵正则化虽然能够减少过拟合问题，但是最好的方法是设计能够新的注意力框架，使得注意力的分布更清晰和稀疏，即关注更多位置的单词




## 2022.09.14

- A Contrastive Cross-Channel Data Augmentation Framework for Aspect-Based Sentiment Analysis
- COLING-2022([Paper](/Paper/2022_09_14_A%20Contrastive%20Cross-Channel%20Data%20Augmentation%20Framework%20for%20Aspect-Based%20Sentiment%20Analysis.pdf))

## 2022.11.02

- Discrete Opinion Tree Induction for Aspect-based Sentiment Analysis
- ACL-2022([Paper](/Paper/2022_11_02_Discrete%20Opinion%20Tree%20Induction%20for%20Aspect-based%20Sentiment%20Analysis.pdf)/[PPT](2022_11_02_dotGCN.pptx))

## 2022.11.30

- Aspect Feature Distillation and Enhancement Network for Aspect-based Sentiment Analysis
- SIGIR-2022([Paper](/Paper/2022_11_30_Aspect%20Feature%20Distillation%20and%20Enhancement%20Network%20for%20Aspect-based%20Sentiment%20Analysis.pdf)/[PPT](/Paper/2022_11_30_AFDEN.pptx))

## 2022.02.27

* Improving aspect-based sentiment analysis with Knowledge-aware Dependency Graph Network
* Information Fusion-2023([Paper](/Paper/2023_02_27_Improving%20aspect-based%20sentiment%20analysis%20with%20Knowledge-aware%20Dependency%20Graph%20Network.pdf))
