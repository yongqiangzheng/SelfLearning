## Learn from structural scope: Improving aspect-level sentiment analysis with hybrid graph convolutional networks

Neurocomputing 2023

> **Abstract**
> 
> Based on the observation that targets and sentiments essentially establish relations following the grammatical hierarchy of **phrase-clause-sentence** structure, it is hopeful to exploit comprehensive syntactic information for better guiding the learning process.
>
> **Introduction**
>
> Scope, which is a well-structured and continuous text region expressing target-specific opinion.
> 
> Compared with opinion span, Scope is characterized by a well-defined structure, which highlights the learning of various syntactic features (e.g., phrase, clause and sentence) related to the target to ensure **structural and semantic completeness**.

1. 方面和情感表达依照“短语-从句-句子”结构建立关系
2. 和观点词span相比，通过学习句法特征保证Scope的结构化和语义完整性

> First, constituency parsing decomposes a sentence into phrases and combines them hierarchically into clauses and sentences, which naturally follows the phrase-clause-sentence structure of Scope and can serve as the foundation to encode structural information. 
>
> Second, dependency parsing is capable of capturing long-range dependencies such as coreference relation, which can help the model obtain the sentence-level connection. As for constituency parsing, it displays the entire sentence structure and relations, while dependency parsing explores relations between words.
> 
> Third, dependency tree can actually not only parse the dependency relations, but also derive constituent boundaries, which is critical for modeling Scope. However, this requires unbounded number of hops over dependency tree to determine the boundaries that entail more layers of networks (e.g., GCN) for obtaining syntactic representations. It would be resource consuming and impractical. In this perspective, constituency tree and dependency tree present two complementary sides of syntactic relations in sentences. 

1. 成分句法分析分解句子，获得层次结构，符合“短语-从句-句子”结构
2. 依存句法分析可以捕获远距离依存，成分分析可以看句子的结构和关系，依存分析可以看单词的关系
3. 依存树也可以划分成分边界，但是依存树的无限深度需要更多的网络层，消耗资源且不切实际
4. 所以要把依存和成分结合互补，学习全面的句法关系