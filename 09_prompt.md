### 文本定年数据集构建

> **You are an Expert in LLM Application and Dataset Engineering.**
>
> **Data Ingestion**
>
> 1. Load raw spreadsheet data using LangChain’s `UnstructuredExcelLoader`, pointing to `data/raw/*.xlsx`, and extract textual content and metadata ([Introduction | 🦜️🔗 LangChain](https://python.langchain.com/docs/integrations/document_loaders/microsoft_excel/?utm_source=chatgpt.com)).
> 2. For each sheet specified (`Sheet1`, `Metadata`), extract columns matching `/text/i` and `/label/i`.
>
> **Preprocessing**
>
> - Clean text: lowercase, remove punctuation, strip whitespace, and eliminate stop‑words.
> - Tokenize using suitable subword tokenizers for both classical and modern text contexts.
>
> **Dataset Construction**
>
> - Structure output as JSONL with fields: `{"id": <unique>, "text": <cleaned_text>, "label": <category>}`.
> - Split into 80% train, 10% validation, 10% test, ensuring stratification by `label`.
>
> **Model Configuration**
>
> 1. Fine‑tune the TongGu model on the instruction‑tuning dataset you created, leveraging Redundancy‑Aware Tuning to prevent forgetting ([arXiv](https://arxiv.org/abs/2407.03937?utm_source=chatgpt.com)).
>
> 2. Use Xinference to launch the tuned TongGu instance:
>
>    ```python
>    from xinference_client import Client  
>    client = Client("http://localhost:8000")  
>    uid = client.launch_model(model_name="TongGu-7B-Instruct", model_engine="instruct", model_type="LLM")  
>    ```
>
>    ([Xinference](https://inference.readthedocs.io/?utm_source=chatgpt.com))
>
> **Evaluation**
>
> - Compute accuracy, precision, recall, and F1 on the test set.
> - Generate and inspect confusion matrices for error analysis.
>
> **Deliverables**
>
> - `data/processed/train.jsonl`, `val.jsonl`, `test.jsonl`
> - Code samples for ingestion, preprocessing, fine‑tuning, and inference.
> - Summary report of dataset statistics and model performance.

This prompt ensures a clear, tool‑oriented workflow for preparing, modeling, and evaluating text datasets with LangChain, TongGu, Xinference, and Excel processing ([LangChain Blog](https://blog.langchain.dev/summarizing-and-querying-data-from-excel-spreadsheets-using-eparse-and-a-large-language-model/?utm_source=chatgpt.com), [Introduction | 🦜️🔗 LangChain](https://python.langchain.com/docs/integrations/providers/xinference/?utm_source=chatgpt.com)).



**你是一位大型语言模型应用与数据集工程专家。**

**数据摄取**

1. 使用 LangChain 的 `UnstructuredExcelLoader` 加载原始表格数据，路径为 `data/raw/*.xlsx`，提取文本内容与元数据（参考：[Introduction | 🦜️🔗 LangChain](https://python.langchain.com/docs/integrations/document_loaders/microsoft_excel/?utm_source=chatgpt.com)）。
2. 对指定的每个工作表（`Sheet1`、`Metadata`），提取列名匹配 `/text/i` 和 `/label/i` 的内容。

**预处理**

- 清洗文本：小写化、去除标点符号、去除多余空格、移除停用词。
- 使用适用于经典与现代文本语境的子词分词器进行分词处理。

**数据集构建**

- 将输出结构化为 JSONL 格式，字段包括：`{"id": <唯一标识符>, "text": <清洗后文本>, "label": <类别>}`。
- 按照标签进行分层抽样，划分为训练集（80%）、验证集（10%）和测试集（10%）。

**模型配置**

1. 在你创建的指令微调数据集上对 TongGu 模型进行微调，采用冗余感知微调以防止遗忘现象（参考：[arXiv](https://arxiv.org/abs/2407.03937?utm_source=chatgpt.com)）。

2. 使用 Xinference 启动微调后的 TongGu 实例：

   ```
   pythonCopyEditfrom xinference_client import Client  
   client = Client("http://localhost:8000")  
   uid = client.launch_model(model_name="TongGu-7B-Instruct", model_engine="instruct", model_type="LLM")  
   ```

   （参考：[Xinference](https://inference.readthedocs.io/?utm_source=chatgpt.com)）

**评估**

- 在测试集上计算准确率、精确率、召回率和 F1 分数。
- 生成并分析混淆矩阵以进行错误分析。

**交付内容**

- `data/processed/train.jsonl`、`val.jsonl`、`test.jsonl`
- 包含摄取、预处理、微调和推理的代码样例。
- 数据集统计信息与模型性能的总结报告。





**你是一位大型语言模型应用与数据集工程专家，需要构建一个用于训练文本定年模型的数据集。该数据集首先需要对目前已有的古文文本进行翻译。**

1. 使用 LangChain 的 `UnstructuredExcelLoader` 加载原始表格数据，提取文本内容与元数据（参考：[Introduction | 🦜️🔗 LangChain](https://python.langchain.com/docs/integrations/document_loaders/microsoft_excel/?utm_source=chatgpt.com)）。给对其中的关键词
2. 对指定的每个工作表提取所需的文本内容。
3. 使用 Langchain 框架 和 TongGu 大模型构建一个能够准确翻译古文文本的程序
4. 将原文和译文存为 json 和 excel 格式

---

如果明白请重述你的任务