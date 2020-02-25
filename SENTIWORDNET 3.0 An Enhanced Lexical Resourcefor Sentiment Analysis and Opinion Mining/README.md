# SENTIWORDNET 3.0: An Enhanced Lexical Resourcefor Sentiment Analysis and Opinion Mining
SentiWordNet3.0：一种用于情感分析和意见挖掘的增强型词汇资源

## Abstract
作者提出用于情感分析和观点挖掘的词汇资源SentiWordNet3.0，是SentiWordNet1.0的改进。它们的相同之处都是根据情感的程度自动标注所有WordNet的同义词集，不同之处是标注不同版本的WordNet(2.0/3.0)和使用的标注算法，SentiWordNet3.0的准确率比SentiWordNet1.0提升约20%

## Introduction
SentiWordNet3.0是对同义词集标注积极、消极和中性分数，同一单词不同释义可能会有不同的分数。三个分数的值在\[0,1]之间，和为1。同义集可能对所有三个类别都具有非零分数，表示同义词集的单词对三种情感的程度。SentiWordNet3.0可以点击[这里](http://sentiwordnet.isti.cnr.it/)使用

## A brief history of SENTIWORDNET
SentiWordNet1.0标注WordNet2.0，SentiWordNet3.0标注WordNet3.0<br>
SentiWordNet1.0使用弱监督、半监督学习算法，SentiWordNet3.0使用半监督学习算法，结果馈送到random-walk，迭代至收敛<br>
SentiWordNet1.0用同义词集的解释作为语义表示用于分类，SentiWordNet3.0用Princeton WordNet Gloss Corpus
