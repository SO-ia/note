## RAG

### RAG 流程

查询语句 — 向量化 — 检索 Top-k 文档 — 拼接上下文 — LLM生成答案

> https://zhuanlan.zhihu.com/p/670322092
>
> https://blog.csdn.net/asialee_bird/article/details/81486700



### 向量数据库

向量数据库是一种专门设计用于存储和查询以向量形式表示的数据的系统，向量是一系列数值。这些向量通常使用机器学习模型（如词嵌入或图像编码器）生成，这些模型将非结构化数据（文本、图像等）转换为捕获其语义或上下文含义的数值表示。向量数据库擅长相似性搜索：给定一个查询向量，它们使用近似最近邻 (ANN) 等算法有效地找到数据集中最相似的向量。这使得它们适用于推荐系统、图像检索或语义文本搜索等任务，在这些任务中，精确的关键词匹配效果不佳。

> https://milvus.org.cn/ai-quick-reference/what-is-a-vector-database-and-how-does-it-apply-to-legal-tech



### Retriever

#### process

一般的 Retriever 流程如下：
1. 文本预处理: 分词(英文-空格，中文-单个字符)，清洗(去噪-HTML标签/特殊字符)
2. 文本嵌入: 将文本转换为固定维度的向量
3. 检索算法:
    - 倒排索引(如 BM25, TF-IDF)
    - 向量检索(如 向量数据库FAISS/Milvus, cos-sim)
    - 混合检索(结合向量检索和倒排索引, 初筛+精筛/综合得分)
4. 结果重排序
    - **相似度**：向量相似度
    - **模型**：排序模型（如 BERT-based ranking model）对候选文档进行排序
    - **混合排序**：多种排序方法 (如先按向量相似度排序，再按关键词匹配度排序)

#### 检索方法

##### BM25

核心思想是基于词频(TF)和逆文档频率(IDF),同时还引入了文档的长度信息来计算文档D和查询Q之间的相关性。

##### FAISS

###### 处理流程

1. 数据预处理 — 文本向量化

   1. 处理：原始向量 (np.ndarray) 转换为 float32 类型
   2. FAISS 只接受 float32

2. 量化器初始化

   1. 定义距离计算方法，如 IndexFlatIP，IndexFlatL2，IndexFlatL2，IndexFlatL2，IndexHNSW，IndexLSH

      ```python
      quantizer = faiss.IndexFlatL2(d)
      ```

   2. 创建基础索引

3. 是否需要训练

   1. 是: 使用k-means聚类训练 (大概需要5-10%的数据)，得到聚类中心
   2. 否: 跳过此步即可

4. 添加数据: 将向量数据加入索引

5. 保存索引文件







## Function calling

大模型将自然语言转换为结构化函数调用指令，充当**自然语言与API的翻译层**。





## PEFT

### LoRA

#### Theory



> [LORA微调系列(一)：LORA和它的基本原理](https://zhuanlan.zhihu.com/p/646791309)
>
> [论文精读：LoRa: Low-Rank Adaptation of Large Language Models](https://zhuanlan.zhihu.com/p/673058387)



#### Practice





> [LLM - LoRA 模型合并与保存_lora merge-CSDN博客](https://blog.csdn.net/BIT_666/article/details/132065177)





## PE

Prompt Engineering





### reference

> [提示工程指南（一）——详解LLM中各个参数的意义 - 百度智能云千帆社区](https://qianfan.cloud.baidu.com/qianfandev/topic/268819)
>
> [Dify LLM 配置参数详解-CSDN博客](https://blog.csdn.net/weixin_44705554/article/details/146458139)
>
> https://milvus.org.cn/ai-quick-reference

