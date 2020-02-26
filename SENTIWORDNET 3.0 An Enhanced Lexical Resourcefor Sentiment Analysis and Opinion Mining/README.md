# SENTIWORDNET 3.0: An Enhanced Lexical Resourcefor Sentiment Analysis and Opinion Mining
SentiWordNet3.0：一种用于情感分析和意见挖掘的增强型词汇资源

## Abstract
作者提出用于情感分析和观点挖掘的词汇资源SentiWordNet3.0，是SentiWordNet1.0的改进。它们的相同之处都是根据情感的程度自动标注所有WordNet的同义词集，不同之处是标注不同版本的WordNet(2.0/3.0)和使用的标注算法，SentiWordNet3.0的准确率比SentiWordNet1.0提升约20%

## Introduction
SentiWordNet3.0是对同义词集标注积极、消极和中性分数，同一单词不同释义可能会有不同的分数。三个分数的值在\[0,1]之间，和为1。同义集可能对所有三个类别都具有非零分数，表示同义词集的单词对三种情感的程度。SentiWordNet3.0可以点击[这里](http://sentiwordnet.isti.cnr.it/)使用

## A brief history of SENTIWORDNET
SentiWordNet1.0标注WordNet2.0<br>
SentiWordNet3.0标注WordNet3.0

SentiWordNet1.0使用弱监督、半监督学习算法<br>
SentiWordNet3.0使用半监督学习算法，结果馈送到random-walk，迭代至收敛

SentiWordNet1.0用同义词集的解释作为语义表示用于分类<br>
SentiWordNet3.0用Princeton WordNet Gloss Corpus作为语义表示用于分类

## Generating SENTIWORDNET 3.0
SentiWordNet3.0有2个过程：半监督学习和random-walk

### The semi-supervised learning step
半监督学习有4个步骤

1.扩展种子集合<br>
初始种子集合由7个典型积极术语集合和7个典型消极术语集合，通过WordNet的二元关系扩展初始种子集合。根据同义关系将术语加入到相同极性的集合，根据反义关系将术语加入到相反极性的集合。通过设置半径k，将集合中的术语在距离为k的所有有同义和反义关系的术语加入到集合里

2.分类器训练<br>
将前面得到的2组同义词集和假定具有Obj属性的另一组同义词集作为训练集用于训练分类器。SentiwordNet3.0使用Princeton WordNet Gloss Corpus的注释，这些注释不是对术语的解释，而是WordNet同义词集序列。该分类器不是对术语的解释而是对同义词集序列作分类，因此也可以将该分类器称为同义词集袋(bag of synsets)模型。SentiWordNet1.0使用的是术语的解释，属于词袋(bag of words)模型

3.同义词集分类<br>
将WordNet所有同义词集（包括步骤2使用的同义词集）输入到分类器分类

4.分类器组合<br>
通过使用不同的半径k={0，2，4，6}和不同的分类算法（Rocchio算法和SVMs）构造8个分类器，将8个分类器的结果取均值得到同义词集的最终极性分数

### The random-walk step
random-walk有2个步骤

1.将WordNet构造为一张图<br>
作者假定两个词存在有向链接，当且仅当一个词出现在另一个词的定义里。作者认为，如果定义一个词的大多数术语是积极的，那么这个被定义的词有很大概率是积极的。换句话说，积极和消极在图中是从定义中使用的术语到被定义的术语这一路径流动的。<br>
然而，在WordNet中同义词集的定义没有语义消歧，没有办法构造上述关系。Princeton WordNet Gloss Corpus正好解决这一问题，每个词的定义都是由同义词集组成的，由此可以构造一张图<br>
random-walk积极和消极分数太小，这会使中性分数非常高，不适合极性分数的生成。作者观察发现，在半监督学习过程中，积极或消极都遵循幂律分布（情感分数越高，同义词集数量越少），因此，作者通过两个幂函数a1*x^b1和a2*x^b2去拟合由图计算得到的分数的分布，而中性分数=1-(积极分数+消极分数)

2.运行迭代直至收敛

## Evaluating SENTIWORDNET 3.0
SentiWordNet3.0选取出Micro-WN(Op)-3.0中的同义词集，与之作比较

### Micro-WN(Op)-3.0
Micro-WN(Op)有1105个的同义词集，由5个人手工标注积极、消极和中性<br>
Micro-WN(Op)(1):   1-110 5个人共同标注<br>
Micro-WN(Op)(2): 111-606 3个人独立标注<br>
Micro-WN(Op)(3): 607-1105 2个人独立标注<br>
Micro-WN(Op)服从WordNet的词性分布，Micro-WN(Op)(x)服从Micro-WN(Op)的词性分布 (x=1,2,3)

作者将SentiWordNet和Micro-WN(Op)(2)(3)作比较，由于Micro-WN(Op)是基于WordNet2.0标注，不能和SentiWordNet3.0直接比较。因此，作者用了3种策略将WordNet2.0的释义映射到WordNet3.0，构造[Micro-WN(Op)-3.0](http://sentiwordnet.isti.cnr.it/)

#### WORDNET sense mappings
WordNet有2.0到3.0的[映射](http://wordnetcode.princeton.edu/3.0/WNsnsmap-3.0.tar.gz)，但仅仅是名词和动词的映射，每个映射都有置信度(0-100)，作者仅选取置信度为100的映射，最终得到269个映射

#### Synset term matching
如果Micro-WN(OP)包含和WordNet3.0完全相同的术语，并且这样的术语集合只出现在WordNet2.0和3.0中的一个S同义词集中，则认为这两个同义词集为同一个

#### Gloss similarity
将Micro-WN(OP)的一个同义词集的注释和WordNet3.0的所有注释计算Dice系数，这种方法最有效

### Evaluation measure
作者使用归一化的Kendall tau距离来比较SentiWordNet和Micro-WN(OP)的相似程度，距离越小，效果越好

## Results
SentiWordNet版本对比<br>
SentiWordNet1.0 vs Micro-WN(OP)<br>
SentiWordNet3.0 vs Micro-WN(OP)-3.0

&nbsp | Positivity | Negativity
-|-|-
SentiWordNet 1.0 | .349 | .296
SentiWordNet 3.0 |.281 (-19.48%) |.231 (-21.96%)

SentiWordNet3.0算法对比<br>
半监督学习 vs 半监督学习+random-walk

&nbsp;|Positivity|Negativity
-|-|-
SentiWordNet 3.0-semi|.339|.286
SentiWordNet 3.0|.281 (-17.11%)|.231 (-19.23%)
