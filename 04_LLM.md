## 训练

### learning record

参考代码：[wyf3/llm_related: 复现大模型相关算法及一些学习记录](https://github.com/wyf3/llm_related)

参考视频：Bilibili — 偷心九月 333

1. 2025.07.13
2. 

### steps

1. 训练 tokenizer



## MoE



## Model

### awq

[大模型(LLM)量化(Quantization)原理学习 - 知乎](https://zhuanlan.zhihu.com/p/29140505773)





## Huggingface

### 基本下载命令

```powershell
huggingface-cli download <模型名称> [文件名]
```

`<模型名称>`：Hugging Face Hub 上的模型仓库名称，例如 bert-base-uncased。
`[文件名]`：（可选）指定要下载的文件名称，例如 config.json。如果不指定文件名，则会下载整个模型仓库。

### 常用参数

1. 指定下载路径

```powershell
huggingface-cli download <模型名称> --local-dir <本地路径>
```

--local-dir：指定下载文件的本地目录。如果没有指定，默认会下载到系统的缓存目录中。

启用断点续传

```powershell
huggingface-cli download <模型名称> --resume-download
```

--resume-download：如果下载中断，可以重新开始下载，而不会从头开始。

下载特定版本的文件

```powershell
huggingface-cli download <模型名称> <文件名> --revision <版本号>
```

--revision：指定要下载的模型版本号。如果不指定，默认下载最新版本。
启用多线程下载（加速下载）

```powershell
huggingface-cli download <模型名称> --num-procs <线程数>
```

--num-procs：指定下载时使用的线程数。默认为单线程，增加线程数可以加速下载。
下载整个模型仓库

```powershell
huggingface-cli download <模型名称>
```

如果不指定文件名，huggingface-cli 会自动下载模型仓库中的所有文件。

#### 示例命令

下载整个模型仓库到默认缓存目录

```powershell
huggingface-cli download bert-base-uncased
```

下载指定文件到默认缓存目录

```powershell
huggingface-cli download bert-base-uncased config.json
```

下载整个模型仓库到指定目录

```powershell
huggingface-cli download bert-base-uncased --local-dir ./models
```

下载指定文件到指定目录

```powershell
huggingface-cli download bert-base-uncased config.json --local-dir ./models
```

下载特定版本的文件

```powershell
huggingface-cli download bert-base-uncased config.json --revision v1.0.0
```

启用断点续传下载 (无需添加)

```powershell
huggingface-cli download bert-base-uncased --resume-download
```

启用多线程下载 (测试为无效参数)

```powershell
huggingface-cli download bert-base-uncased --num-procs 4
```

#### 其他注意事项

登录账号：如果需要下载私有模型或上传模型，需要先登录 Hugging Face 账号：

```powershell
huggingface-cli login
```

配置国内镜像：国内用户可以配置 Hugging Face 的国内镜像源以加速下载：

```powershell
export HF_ENDPOINT=https://hf-mirror.com
```

或在 Windows 中：

```powershell
$env:HF_ENDPOINT = "https://hf-mirror.com"
```

通过以上指令和参数，你可以灵活地从 Hugging Face Hub 下载模型和文件。



### 模型

#### 加载 embedding 模型

```python
from langchain_huggingface import HuggingFaceEmbeddings
embeddings = HuggingFaceEmbeddings(model_name='/path/to/model/dir')
```

如果出现以下报错, 即模型文件夹内缺少几个 `config.json`  配置文件

```powershell
No sentence-transformers model found with name ./models/bert-base-chinese. Creating a new one with mean pooling.
```

但目前 `bert-base-chinese` 模型还未找到对应的 pooling 配置文件

> 下次可参考
> https://blog.csdn.net/m0_46696145/article/details/145936578







## LangChain

https://zhuanlan.zhihu.com/p/656646499

### langchain 官方文档

eng

https://python.langchain.com/docs/introduction/

chinese

http://langchain.ichuangpai.com/



### pydantic 报错

#### error

```bash
Traceback (most recent call last):
  File "gci-K.py", line 903, in <module>
    extract_keywords(addr, fact_original, accu_clean,
  File "gci-K.py", line 114, in extract_keywords
    import spacy
  File "/root/miniconda3/lib/python3.8/site-packages/spacy/__init__.py", line 14, in <module>
    from . import pipeline  # noqa: F401
  File "/root/miniconda3/lib/python3.8/site-packages/spacy/pipeline/__init__.py", line 1, in <module>
    from .attributeruler import AttributeRuler
  File "/root/miniconda3/lib/python3.8/site-packages/spacy/pipeline/attributeruler.py", line 6, in <module>
    from .pipe import Pipe
  File "spacy/pipeline/pipe.pyx", line 1, in init spacy.pipeline.pipe
  File "spacy/vocab.pyx", line 1, in init spacy.vocab
  File "/root/miniconda3/lib/python3.8/site-packages/spacy/tokens/__init__.py", line 1, in <module>
    from .doc import Doc
  File "spacy/tokens/doc.pyx", line 36, in init spacy.tokens.doc
  File "/root/miniconda3/lib/python3.8/site-packages/spacy/schemas.py", line 6, in <module>
    from pydantic import StrictStr, StrictInt, StrictFloat, StrictBool, ConstrainedStr
  File "/root/miniconda3/lib/python3.8/site-packages/pydantic/__init__.py", line 412, in __getattr__
    return _getattr_migration(attr_name)
  File "/root/miniconda3/lib/python3.8/site-packages/pydantic/_migration.py", line 302, in wrapper
    raise PydanticImportError(f'`{import_path}` has been removed in V2.')
pydantic.errors.PydanticImportError: `pydantic:ConstrainedStr` has been removed in V2.

For further information visit https://errors.pydantic.dev/2.10/u/import-error
```

#### solution

检查 pydantic 版本

```bash
pip list | grep pydantic

pydantic                       2.10.6
pydantic-core                  2.27.2
```

https://zhuanlan.zhihu.com/p/693884344

```bash
#需要降低版本到 pydantic==1.10.13 pydantic_core==2.14.6
pip install pydantic==1.10.13 pydantic_core==2.14.6
```



### langchain-ollama 与 pydantic 不兼容

#### error

```bash
Traceback (most recent call last):
  File "02.py", line 4, in <module>
    from langchain_ollama import ChatOllama
  File "/root/miniconda3/lib/python3.8/site-packages/langchain_ollama/__init__.py", line 3, in <module>
    from langchain_ollama.chat_models import ChatOllama
  File "/root/miniconda3/lib/python3.8/site-packages/langchain_ollama/chat_models.py", line 42, in <module>
    from ollama import AsyncClient, Client, Message, Options
  File "/root/miniconda3/lib/python3.8/site-packages/ollama/__init__.py", line 1, in <module>
    from ollama._client import AsyncClient, Client
  File "/root/miniconda3/lib/python3.8/site-packages/ollama/_client.py", line 25, in <module>
    from pydantic.json_schema import JsonSchemaValue
ModuleNotFoundError: No module named 'pydantic.json_schema'
```

#### solution

```bash
# 安装指定版本（需验证与ollama的兼容性）
pip install "pydantic<2.0" "langchain-ollama==0.1.3"  # 选择已知兼容版本

# output
pip install "pydantic<2.0" "langchain-ollama==0.1.3"
Looking in indexes: https://repo.huaweicloud.com/repository/pypi/simple
Requirement already satisfied: pydantic<2.0 in /root/miniconda3/lib/python3.8/site-packages (1.10.13)
Requirement already satisfied: langchain-ollama==0.1.3 in /root/miniconda3/lib/python3.8/site-packages (0.1.3)
...
(详见 ./log/04_xinference_log.md—7)
...
```

##### before

```
pip list | grep langchain
langchain                      0.2.17
langchain-community            0.2.19
langchain-core                 0.2.43
langchain-ollama               0.1.3
langchain-text-splitters       0.2.4
```

##### after

```
pip list | grep langchain
langchain                      0.2.17
langchain-community            0.2.19
langchain-core                 0.2.43
langchain-ollama               0.1.3
langchain-text-splitters       0.2.4
```









## RAGAS

### 1 prompt

<font color= RED> 未解决 </font>

```python
No module named 'ragas.llms.prompt' to create custom Prompt for any metrics 
```

> [No module named 'ragas.llms.prompt' to create custom Prompt for any metrics · Issue #1726 · explodinggradients/ragas](https://github.com/explodinggradients/ragas/issues/1726)





```
Prompt fix_output_format failed to parse output: The output parser failed to parse the output including retries.
Prompt fix_output_format failed to parse output: The output parser failed to parse the output including retries.
Prompt fix_output_format failed to parse output: The output parser failed to parse the output including retries.
Prompt statement_generator_prompt failed to parse output: The output parser failed to parse the output including retries.
Exception raised in Job[0]: RagasOutputParserException(The output parser failed to parse the output including retries.)
```





## ML

### CN 卷积

#### 概念解释

##### 上采样 upsampled

1. 作用：
   1. 放大图片
   2. 增加图片分辨率



##### 下采样



# Bottom