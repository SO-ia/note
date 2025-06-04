## Error

### 1

```powershell
无法加载文件 D:\A_Project\0_Test\.venv\Scripts\Activate.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft. com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
```

#### solution

第一步：以管理员身份运行 powershell
第二步：执行：get-ExecutionPolicy 回复 Restricted，表示状态是禁止的。
第三步：执行：set-ExecutionPolicy RemoteSigned
第四步：选择 Y，回车
如果第二步执行完成出现报错，可以忽略继续执行后续的步骤

```powershell
PS C:\Users\%username%> get-ExecutionPolicy
Restricted
PS C:\Users\%username%> set-ExecutionPolicy RemoteSigned
PS C:\Users\%username%> get-ExecutionPolicy
RemoteSigned
```

https://blog.csdn.net/weixin_44670563/article/details/108399019?fromshare = blogdetail&sharetype = blogdetail&sharerId = 108399019&sharerefer = PC&sharesource = qq_73921758&sharefrom = from_link



### 2



### 3 模型加载

#### bert_score 无法加载本地模型

[解决：bert_score 无法加载本地模型_bertscore 使用本地模型-CSDN 博客](https://blog.csdn.net/nlhkfcdxb/article/details/140063671)

使用方法一修改源码如下

源码路径：`D:\A_Project\0_Test\.venv\Lib\site-packages\bert_score\utils.py`

即将 `model_type` 修改为本地下载的模型路径 `model_path`

```python
def get_model(model_type, num_layers, all_layers=None):
model_path="models/bert-base-chinese"
if model_type.startswith("scibert"):
model = AutoModel.from_pretrained(cache_scibert(model_type))
elif "t5" in model_type:
from transformers import T5EncoderModel

# model = T5EncoderModel.from_pretrained(model_type)
model = T5EncoderModel.from_pretrained(model_path)
else:
# model = AutoModel.from_pretrained(model_type)
model = AutoModel.from_pretrained(model_path)
model.eval()
```

```python
def get_tokenizer(model_type, use_fast=False):
if model_type.startswith("scibert"):
model_type = cache_scibert(model_type)

model_path="models/bert-base-chinese"
if version.parse(trans_version) >= version.parse("4.0.0"):
# tokenizer = AutoTokenizer.from_pretrained(model_type, use_fast=use_fast)
tokenizer = AutoTokenizer.from_pretrained(model_path, use_fast=use_fast)
else:
assert not use_fast, "Fast tokenizer is not available for version < 4.0.0"
# tokenizer = AutoTokenizer.from_pretrained(model_type)
tokenizer = AutoTokenizer.from_pretrained(model_path)

return tokenizer
```



### 4 模型下载

#### HF models

##### 1 bert-base-chinese

1. 无模型报错

   ```python
   Traceback (most recent call last):
   File "bert_1.py", line 172, in <module>
   main()
   File "bert_1.py", line 156, in main
   tokenizer = BertTokenizer.from_pretrained("bert-base-chinese")
   File "/root/miniconda3/lib/python3.8/site-packages/transformers/tokenization_utils_base.py", line 1838, in from_pretrained
   raise EnvironmentError(
   OSError: Can't load tokenizer for 'bert-base-chinese'. If you were trying to load it from 'https://huggingface.co/models', make sure you don't have a local directory with the same name. Otherwise, make sure 'bert-base-chinese' is the correct path to a directory containing all relevant files for a BertTokenizer tokenizer.
   ```

2. 模型下载网络连接报错

   ```
   
   ```

3. solution

   ```bash
   export HF_ENDPOINT=https://hf-mirror.com
   
   huggingface-cli download bert-base-chinese --local-dir /root/autodl-tmp/data/models/tmp --local-dir-use-symlinks False
   
   # 但不知道为啥下面两个就下载不了，总显示报错
   huggingface-cli download lexlms/legal-roberta-base --local-dir /root/autodl-tmp/data/models/legal-roberta-base --local-dir-use-symlinks False
   huggingface-cli download bert-base-chinese --local-dir /root/autodl-tmp/data/models --local-dir-use-symlinks False
   ```

4. `bert-base-chinese` 下载完成提示

   ```bash
   (base) root@autodl-container-xxxxx:~/autodl-tmp/traditional# huggingface-cli download bert-base-chinese --local-dir /root/autodl-tmp/data/models/bert-base-chinese --local-dir-use-symlinks False
   /root/miniconda3/lib/python3.8/site-packages/huggingface_hub/commands/download.py:139: FutureWarning: Ignoring --local-dir-use-symlinks. Downloading to a local directory does not use symlinks anymore.
   warnings.warn(
   Fetching 10 files: 0%|| 0/10 [00:00<?, ?it/s]Downloading 'model.safetensors' to '/root/autodl-tmp/data/models/.cache/huggingface/download/xGOKKLRSlIhH692hSVvI1-gpoa8=.3404a1ffd8da507042e8161013ba2a4fc49858b4e3f8fbf5ce5724f94883aec3.incomplete'
   Downloading 'tf_model.h5' to '/root/autodl-tmp/data/models/.cache/huggingface/download/a7eHxRFT3OeMBIFg52k2nfj5m7w=.612acd33db45677c3d6ba70615336619dc65cddf1ecf9d39a22dd1934af4aff2.incomplete'
   Downloading 'flax_model.msgpack' to '/root/autodl-tmp/data/models/.cache/huggingface/download/gPcsVCQDYDHk-_n0G9uADl7PXIM=.76df8425215fb9ede22e0393e356f82a99d84e79f078cd141afbbf9277460c8e.incomplete'
   Downloading '.gitattributes' to '/root/autodl-tmp/data/models/.cache/huggingface/download/wPaCkH-WbT7GsmxMKKrNZTV4nSM=.602b71f15d40ed68c5f96330e3f3175a76a32126.incomplete'
   Downloading 'README.md' to '/root/autodl-tmp/data/models/.cache/huggingface/download/Xn7B-BWUGOee2Y6hCZtEhtFu4BE=.048fdf63b2740ccf860ad1e5b4287ccbac89869a.incomplete'
   README.md: 1.85kB [00:00, 300kB/s] 
   Download complete. Moving file to /root/autodl-tmp/data/models/README.md | 0.00/959 [00:00<?, ?B/s]
   Downloading 'pytorch_model.bin' to '/root/autodl-tmp/data/models/.cache/huggingface/download/Q1p2l2BzM1m6P5jKvr8WTq1TUio=.8a693db616eaf647ed2bfe531e1fa446637358fc108a8bf04e8d4db17e837ee9.incomplete'
   Downloading 'tokenizer_config.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/vzaExXFZNBay89bvlQv-ZcI6BTg=.2ba5de7675473164e07f3b3531748c9a6f113a2c.incomplete'
   Downloading 'config.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/8_PA_wEVGiVa2goH2H4KQOQpvVY=.a521dc2845bdddbe822864290c6b928396fc5ee8.incomplete'
   .gitattributes: 100%|███████████████████████████████████████████████| 445/445 [00:00<00:00, 80.6kB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/.gitattributes0.00/445 [00:00<?, ?B/s]
   Fetching 10 files:10%|████▌ | 1/10 [00:01<00:09,1.04s/it]Downloading 'tokenizer.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/HgM_lKo9sdSCfRtVg7MMFS7EKqo=.dd9401af0a4713df0e75066ae78d5bf6fa6c7116.incomplete'
   tokenizer_config.json: 100%|██████████████████████████████████████| 49.0/49.0 [00:00<00:00, 9.00kB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/tokenizer_config.jsonM [00:00<?, ?B/s]
   config.json: 624B [00:00, 113kB/s] 
   Download complete. Moving file to /root/autodl-tmp/data/models/config.json| 0.00/49.0 [00:00<?, ?B/s]
   Fetching 10 files:30%|█████████████▊| 3/10 [00:01<00:02,2.84it/s]Downloading 'vocab.txt' to '/root/autodl-tmp/data/models/.cache/huggingface/download/E2zehc7lrIVb8gRdx7qjK54iiZY=.ca4f9781030019ab9b253c6dcb8c7878b6dc87a5.incomplete'
   tokenizer.json: 269kB [00:00, 1.55MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/tokenizer.json
   vocab.txt: 110kB [00:00, 670kB/s] 
   Download complete. Moving file to /root/autodl-tmp/data/models/vocab.txt| 0.00/478M [00:00<?, ?B/s]
   model.safetensors: 100%|██████████████████████████████████████████| 412M/412M [01:40<00:00, 4.11MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/model.safetensors1:40<00:00, 4.24MB/s]
   tf_model.h5: 100%|████████████████████████████████████████████████| 478M/478M [01:52<00:00, 4.26MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/tf_model.h578M [01:39<00:23, 5.74MB/s]
   (…)e356f82a99d84e79f078cd141afbbf9277460c8e: 100%|████████████████| 409M/409M [02:08<00:00, 3.18MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/flax_model.msgpack:52<00:00, 10.5MB/s]
   pytorch_model.bin: 100%|██████████████████████████████████████████| 412M/412M [05:32<00:00, 1.24MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/pytorch_model.bin1:49<00:56, 1.15MB/s]
   Fetching 10 files: 100%|█████████████████████████████████████████████| 10/10 [05:33<00:00, 33.37s/it]
   /root/autodl-tmp/data/models
   (base) root@autodl-container-19b1118252-be2efcfc:~/autodl-tmp/traditional# 
   pytorch_model.bin: 100%|███████████████████████████████████████████| 412M/412M [05:32<00:00, 382kB/s]
   ```

5. 这次的模型路径可以直接通过 model_path 传入，不需要修改包内代码



##### 2 lexlms/legal-roberta-base

1. 修改环境变量后仍使用原始网址请求，出现报错

2. 只能通过可访问原网站或镜像网站的电脑手动下载使用

3. 直接传入 model_path 即可使用

   



### 5

#### error

Import "tensorflow.keras.layers" could not be resolved Pylance reportMissingImports

![3](assets\3.png)

#### solution

**layers**

```python
from tensorflow_core.python.keras import layers
```

**optimizers**

```python
from tensorflow_core.python.keras.api._v2.keras import optimizers
```



### 6 HTTP 错误码

解析 HTTP 错误码 400 Bad Request 及其常见原因与解决方法
1. 引言
    在进行 web 开发过程中，我们经常会遇到各种 HTTP 错误码。HTTP 错误码用于表示服务器对请求的响应状态，帮助我们定位和解决问题。本文将重点解析 HTTP 错误码 400 Bad Request，探讨其常见原因和解决方法。
    
    HTTP 错误码的作用和分类
    HTTP 错误码是由服务器返回给客户端的状态码，用于表示请求的处理状态。它们按照类别分为以下五类：
    
    1xx：信息，表示服务器已接收到请求并且正在处理。
    2xx：成功，表示服务器成功处理了请求。
    3xx：重定向，表示需要进一步操作以完成请求。
    4xx：客户端错误，表示服务器无法处理请求。
    5xx：服务器错误，表示服务器在处理请求时发生了错误。
    400 Bad Request 错误的含义
    400 Bad Request 错误表示服务器无法理解客户端发送的请求，原因通常是由于客户端发送的请求存在问题。本文将重点分析 400 Bad Request 错误的常见原因和解决方法。
    
2. 400 Bad Request 错误的常见原因
    400 Bad Request 错误可能由多种原因引起。下面列举了一些常见的原因：

    参数错误
    缺少必要参数：客户端未提供必要的参数，导致服务器无法处理请求。
    参数格式不正确：客户端提供的参数格式不符合服务器的要求。
    参数超出范围：客户端提供的参数超出了服务器允许的范围。
    请求格式错误
    错误的请求头：客户端发送的请求头不符合 HTTP 协议规范。
    错误的请求方法：客户端使用了服务器不支持的请求方法。
    错误的请求体格式：客户端发送的请求体格式不符合服务器的要求。
    请求长度超过限制
    服务器限制请求长度的原因：服务器为了防止恶意请求或保证服务器性能，设置了请求长度的限制。
    如何解决请求长度超过限制的问题：客户端需要根据服务器的要求，合理控制请求长度。
    URL 格式错误
    缺少或错误的协议头：客户端未指定请求的协议头，或者指定了错误的协议头。
    缺少或错误的域名：客户端未提供请求的域名，或者提供了错误的域名。
    缺少或错误的路径：客户端未提供请求的路径，或者提供了错误的路径。
    在后续的章节中，我们将分别详细讨论这些常见原因以及解决方法。

3. 参数错误导致的 400 Bad Request 错误
    在进行 web 开发中，参数错误是导致 400 Bad Request 错误的常见原因之一。下面将具体讨论几种常见的参数错误情况。

    缺少必要参数
    缺少必要参数是导致 400 Bad Request 错误的常见原因之一。当客户端未提供服务器需要的参数时，服务器无法进行请求处理。为了解决这个问题，客户端需要确保提供了所有必要的参数。

    参数格式不正确
    参数格式不正确也是导致 400 Bad Request 错误的常见原因之一。服务器在处理请求时，期望参数的格式是符合特定规范的，如果客户端提供的参数格式不符合规范，服务器将无法理解请求。为了解决这个问题，客户端需要确保提供的参数格式与服务器要求一致。

    参数超出范围
    参数超出范围是导致 400 Bad Request 错误的另一个常见原因。服务器通常会对参数设置一些限制，例如数值范围、字符串长度等。如果客户端提供的参数超出了服务器允许的范围，服务器将无法处理请求。为了解决这个问题，客户端需要确保提供的参数在合理的范围内。

    在实际开发中，可以通过对参数进行校验和验证来避免参数错误导致的 400 Bad Request 错误。例如，可以使用正则表达式或自定义函数对参数进行格式校验，使用条件语句判断参数是否缺失或超出范围。

4. 请求格式错误导致的 400 Bad Request 错误
    除了参数错误，请求格式错误也是导致 400 Bad Request 错误的常见原因之一。下面将具体讨论几种常见的请求格式错误情况。

    错误的请求头
    请求头是客户端向服务器发送请求时携带的一些元数据信息，例如 Content-Type、Authorization 等。如果客户端发送的请求头不符合 HTTP 协议规范或服务器的要求，服务器将无法正确处理请求。为了解决这个问题，客户端应确保发送的请求头是正确的，并符合服务器的要求。

    错误的请求方法
    HTTP 协议定义了一些常见的请求方法，例如 GET、POST、PUT、DELETE 等。服务器根据不同的请求方法执行相应的操作。如果客户端使用了服务器不支持的请求方法，服务器将返回 400 Bad Request 错误。为了解决这个问题，客户端需要使用服务器支持的请求方法。

    错误的请求体格式
    请求体是客户端向服务器发送请求时携带的数据，例如表单数据、JSON 数据等。如果客户端发送的请求体格式不符合服务器的要求，服务器将无法正确解析请求体。为了解决这个问题，客户端应确保发送的请求体格式与服务器的要求一致。

    在实际开发中，可以使用浏览器的开发者工具或网络抓包工具查看请求的头部和体部，以便定位请求格式错误的问题。同时，也可以参考服务器的文档或规范，了解服务器对请求格式的要求。

5. 请求长度超过限制导致的 400 Bad Request 错误
    有时候，客户端发送的请求长度可能超过了服务器的限制，导致服务器返回 400 Bad Request 错误。下面将讨论请求长度超过限制的原因以及解决方法。

    服务器限制请求长度的原因
    服务器限制请求长度的主要原因是为了防止恶意请求或保证服务器性能。如果服务器允许接收过长的请求，可能会导致服务器资源耗尽、拒绝服务等问题。

    如何解决请求长度超过限制的问题
    为了解决请求长度超过限制的问题，客户端需要根据服务器的要求，合理控制请求长度。可以通过以下几种方式来实现：

    分块请求：将较长的请求拆分成多个较短的请求，分多次发送给服务器。
    压缩请求体：使用压缩算法对请求体进行压缩，减小请求体的大小。
    使用流式传输：对于大文件或大数据量的请求，可以使用流式传输，避免一次性发送全部数据。
    使用合适的数据格式：选择合适的数据格式，例如使用二进制格式代替文本格式，可以减小请求体的大小。
    需要注意的是，客户端在控制请求长度时，也需要考虑服务器对请求长度的限制。可以参考服务器的文档或规范，了解服务器对请求长度的限制，并根据实际情况进行调整。

6. URL 格式错误导致的 400 Bad Request 错误
    URL 格式错误也是导致 400 Bad Request 错误的常见原因之一。下面将具体讨论几种常见的 URL 格式错误情况。

    缺少或错误的协议头
    URL 应包含协议头，例如 http://或 https://。如果客户端未提供或提供了错误的协议头，服务器将无法正确解析 URL。为了解决这个问题，客户端应确保提供正确的协议头。

    缺少或错误的域名
    URL 应包含域名，用于指定要访问的服务器。如果客户端未提供或提供了错误的域名，服务器将无法正确解析 URL。为了解决这个问题，客户端应确保提供正确的域名。

    缺少或错误的路径
    URL 应包含路径，用于指定要访问的资源的位置。如果客户端未提供或提供了错误的路径，服务器将无法正确解析 URL。为了解决这个问题，客户端应确保提供正确的路径。

    在实际开发中，可以使用 URL 解析库或正则表达式对 URL 进行解析和验证，以确保 URL 的格式是正确的。

7. 解决 400 Bad Request 错误的方法
    针对不同的原因，解决 400 Bad Request 错误的方法也不同。下面总结了一些通用的解决方法：

    检查参数和请求格式：确保提供了所有必要的参数，并且参数格式符合服务器要求。同时，也要确保请求头、请求方法和请求体格式正确。
    检查请求长度：根据服务器的要求，合理控制请求长度，避免超过服务器限制。
    检查 URL 格式：确保 URL 包含正确的协议头、域名和路径。
    在解决 400 Bad Request 错误时，可以结合使用浏览器的开发者工具、服务器的日志和相关文档，以便更好地定位和解决问题。

8. 结论
    本文详细解析了 HTTP 错误码 400 Bad Request 及其常见原因与解决方法。通过了解参数错误、请求格式错误、请求长度超过限制和 URL 格式错误等原因，我们可以更好地理解和解决 400 Bad Request 错误。在实际开发中，合理校验参数、检查请求格式、控制请求长度和验证 URL 格式，可以有效避免 400 Bad Request 错误的发生。

9. 参考资料
    HTTP/1.1 协议规范：https://www.w3.org/Protocols/rfc2616/rfc2616.html
    Mozilla 开发者网络：https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400





### 7

> [LLM - CUDA out of memory. 到底怎么事_vllm cuda out of memory-CSDN 博客](https://blog.csdn.net/BIT_666/article/details/132182360)
>
> [vllm 运行过程中出现 cuda out of memory_vllm cuda out of memory-CSDN 博客](https://blog.csdn.net/lanyan90/article/details/146566610)





## download







## packages

### wandb

```python
Some weights of BertForSequenceClassification were not initialized from the model checkpoint at bert-base-chinese and are newly initialized: ['classifier.bias', 'classifier.weight']
You should probably TRAIN this model on a down-stream task to be able to use it for predictions and inference.
wandb: WARNING The `run_name` is currently set to the same value as `TrainingArguments.output_dir`. If this was not intended, please specify a different run name by setting the `TrainingArguments.run_name` parameter.
wandb: Logging into wandb.ai. (Learn how to deploy a W&B server locally: https://wandb.me/wandb-server)
wandb: You can find your API key in your browser here: https://wandb.ai/authorize?ref=models
wandb: Paste an API key from your profile and hit enter:
```

##### solution1: 禁用 `wandb`

```python
import os

# 禁用wandb的环境变量设置
os.environ["WANDB_DISABLED"] = "true"
```

##### solution2: 获取 API

1. https://wandb.ai/authorize?ref = models
2. github 账号登录授权
   ![0](assets\python\0.png)
3. 

> https://blog.csdn.net/weixin_53538865/article/details/136390750



### Accelerator

```bash
TypeError: Accelerator.__init__() got an unexpected keyword argument 'dispatch_batches
```

##### solution

```bash
pip install accelerate==0.28.0
```





### CRF

CRF 在 python 内有多个封装形式

#### 1. TorchCRF

```python
# 安装
pip install TorchCRF

#安装完成
Successfully installed torchcrf-1.1.0

# 使用
from TorchCRF import CRF
```

###### error

```bash
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
Input In [27], in <cell line: 15>()
 13 train_evaluate_loop(texts, labels, size, label_encoder)
 15 if __name__ == "__main__":
---> 16 main()

Input In [27], in main()
 10 for size in test_sizes:
 11 # for dataset_name in DATASET_CONFIG.keys():
 12 print(f"\n{'='*30} Testing with train/test split {1-size:.1f}/{size:.1f} {'='*30}")
---> 13 train_evaluate_loop(texts, labels, size, label_encoder)

Input In [26], in train_evaluate_loop(texts, labels, test_size, label_encoder)
 13 print("loading model...")
 14 tokenizer = BertTokenizer.from_pretrained(MODEL_PATH)
---> 15 model = BertCRF(len(label_encoder.classes_))
 16 device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
 17 model.to(device)

Input In [20], in BertCRF.__init__(self, num_labels)
6 self.dropout = nn.Dropout(0.1)
7 self.classifier = nn.Linear(768, num_labels)
----> 8 self.crf = CRF(num_labels, batch_first=True)

TypeError: __init__() got an unexpected keyword argument 'batch_first'
```

###### solution

如下



#### 2. pytorch-crf







```python
# 安装
pip install pytorch-crf

#安装完成
Looking in indexes: https://repo.huaweicloud.com/repository/pypi/simple
Collecting pytorch-crf
Downloading https://repo.huaweicloud.com/repository/pypi/packages/96/7d/4c4688e26ea015fc118a0327e5726e6596836abce9182d3738be8ec2e32a/pytorch_crf-0.7.2-py3-none-any.whl (9.5 kB)
Installing collected packages: pytorch-crf
Successfully installed pytorch-crf-0.7.2


# 使用
from torchcrf import CRF
```

目前无报错

> https://blog.csdn.net/qq_45041871/article/details/123230255















### pandas









### Torch

#### tolist() 方法使用

```python
def convert_to_list(x):
    
    if isinstance(x, torch.Tensor):
        return x.tolist()
    elif isinstance(x, (tuple, list)):
        return [convert_to_list(item) for item in x]
    elif isinstance(x, str):
        # try:
        # 尝试将字符串转换为张量
        tensor = torch.tensor(eval(x))
        return tensor.tolist()
        # except:
        #     return x.tolist()
    else:
        return x.tolist()
```







### transformers

```python
2025-05-25 21:32:16.223129: I tensorflow/core/util/port.cc:110] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
2025-05-25 21:32:16.276311: I tensorflow/core/platform/cpu_feature_guard.cc:182] This TensorFlow binary is optimized to use available CPU instructions in performance-critical operations.
To enable the following instructions: AVX2 AVX512F AVX512_VNNI FMA, in other operations, rebuild TensorFlow with the appropriate compiler flags.
2025-05-25 21:32:17.091248: W tensorflow/compiler/tf2tensorrt/utils/py_utils.cc:38] TF-TRT Warning: Could not find TensorRT
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)
File ~/miniconda3/lib/python3.8/site-packages/transformers/utils/import_utils.py:1130, in _LazyModule._get_module(self, module_name)
   1129 try:
-> 1130     return importlib.import_module("." + module_name, self.__name__)
   1131 except Exception as e:

File ~/miniconda3/lib/python3.8/importlib/__init__.py:127, in import_module(name, package)
    126         level += 1
--> 127 return _bootstrap._gcd_import(name[level:], package, level)

File <frozen importlib._bootstrap>:1014, in _gcd_import(name, package, level)

File <frozen importlib._bootstrap>:991, in _find_and_load(name, import_)

File <frozen importlib._bootstrap>:975, in _find_and_load_unlocked(name, import_)

File <frozen importlib._bootstrap>:671, in _load_unlocked(spec)

File <frozen importlib._bootstrap_external>:848, in exec_module(self, module)

File <frozen importlib._bootstrap>:219, in _call_with_frames_removed(f, *args, **kwds)

File ~/miniconda3/lib/python3.8/site-packages/transformers/models/bert/modeling_tf_bert.py:30, in <module>
     29 from ...activations_tf import get_tf_activation
---> 30 from ...modeling_tf_outputs import (
     31     TFBaseModelOutputWithPastAndCrossAttentions,
     32     TFBaseModelOutputWithPoolingAndCrossAttentions,
     33     TFCausalLMOutputWithCrossAttentions,
     34     TFMaskedLMOutput,
     35     TFMultipleChoiceModelOutput,
     36     TFNextSentencePredictorOutput,
     37     TFQuestionAnsweringModelOutput,
     38     TFSequenceClassifierOutput,
     39     TFTokenClassifierOutput,
     40 )
     41 from ...modeling_tf_utils import (
     42     TFCausalLanguageModelingLoss,
     43     TFMaskedLanguageModelingLoss,
   (...)
     53     unpack_inputs,
     54 )

File ~/miniconda3/lib/python3.8/site-packages/transformers/modeling_tf_outputs.py:27, in <module>
     23 from .utils import ModelOutput
     26 @dataclass
---> 27 class TFBaseModelOutput(ModelOutput):
     28     """
     29     Base class for model's outputs, with potential hidden states and attentions.
     30 
   (...)
     44             heads.
     45     """

File ~/miniconda3/lib/python3.8/site-packages/transformers/utils/generic.py:258, in ModelOutput.__init_subclass__(cls)
    257 if is_torch_available():
--> 258     import torch.utils._pytree
    260     torch.utils._pytree._register_pytree_node(
    261         cls,
    262         torch.utils._pytree._dict_flatten,
    263         lambda values, context: cls(**torch.utils._pytree._dict_unflatten(values, context)),
    264     )

File ~/miniconda3/lib/python3.8/site-packages/torch/__init__.py:229, in <module>
    228         _load_global_deps()
--> 229     from torch._C import *  # noqa: F403
    231 # Appease the type checker; ordinarily this binding is inserted by the
    232 # torch._C module initialization code in C

ImportError: /root/miniconda3/lib/python3.8/site-packages/torch/lib/libtorch_cuda.so: undefined symbol: cudaGraphInstantiateWithFlags, version libcudart.so.11.0

The above exception was the direct cause of the following exception:

RuntimeError                              Traceback (most recent call last)
Input In [2], in <cell line: 8>()
      6 from sklearn.preprocessing import LabelEncoder
      7 from sklearn.metrics import classification_report
----> 8 from transformers import BertTokenizer, TFBertForSequenceClassification
      9 from transformers import DataCollatorWithPadding
     10 from transformers import create_optimizer

File <frozen importlib._bootstrap>:1039, in _handle_fromlist(module, fromlist, import_, recursive)

File ~/miniconda3/lib/python3.8/site-packages/transformers/utils/import_utils.py:1121, in _LazyModule.__getattr__(self, name)
   1119 elif name in self._class_to_module.keys():
   1120     module = self._get_module(self._class_to_module[name])
-> 1121     value = getattr(module, name)
   1122 else:
   1123     raise AttributeError(f"module {self.__name__} has no attribute {name}")

File ~/miniconda3/lib/python3.8/site-packages/transformers/utils/import_utils.py:1120, in _LazyModule.__getattr__(self, name)
   1118     value = self._get_module(name)
   1119 elif name in self._class_to_module.keys():
-> 1120     module = self._get_module(self._class_to_module[name])
   1121     value = getattr(module, name)
   1122 else:

File ~/miniconda3/lib/python3.8/site-packages/transformers/utils/import_utils.py:1132, in _LazyModule._get_module(self, module_name)
   1130     return importlib.import_module("." + module_name, self.__name__)
   1131 except Exception as e:
-> 1132     raise RuntimeError(
   1133         f"Failed to import {self.__name__}.{module_name} because of the following error (look up to see its"
   1134         f" traceback):\n{e}"
   1135     ) from e

RuntimeError: Failed to import transformers.models.bert.modeling_tf_bert because of the following error (look up to see its traceback):
/root/miniconda3/lib/python3.8/site-packages/torch/lib/libtorch_cuda.so: undefined symbol: cudaGraphInstantiateWithFlags, version libcudart.so.11.0
```







# Bottom