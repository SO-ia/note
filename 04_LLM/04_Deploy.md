## Xinference

[xinference](https://github.com/Nymbo/xinference)

Replace OpenAI GPT with another LLM in your app by changing a single line of code. Xinference gives you the freedom to use any LLM you need. With Xinference, you're empowered to run inference with any open-source language models, speech recognition models, and multimodal models, whether in the cloud, on-premises, or even on your laptop.

> 官方文档
>
> https://inference.readthedocs.io/zh-cn/latest/index.html

### Installation

```powershell
pip install "xinference[all]"
```

#### useful commands

```bash
# 启动 xinference
xinference-local --host 0.0.0.0 --port 9997
# 列出所有 Xinference 支持的指定类型的模型：
xinference registrations -t LLM
# 列出所有在运行的模型：
xinference list
# 停止某个正在运行的模型：
xinference terminate --model-uid "qwen2"
#https://hf-mirror.com/ 
export HF_ENDPOINT=https://hf-mirror.com
export XINFERENCE_MODEL_SRC=modelscope
#log缓存地址
export XINFERENCE_HOME=/root/autodl-tmp
#端口修改了重新设置环境变量
export XINFERENCE_ENDPOINT=http://0.0.0.0:7863
# 通过环境变量临时变更模型下载路径
export XINFERENCE_CACHE_DIR=/root/autodl-tmp/models


# win
# cmd
set HF_ENDPOINT=https://hf-mirror.com
# ps
$env:HF_ENDPOINT = "https://hf-mirror.com"
```

> https://cloud.tencent.com/developer/article/2445726
>
> https://juejin.cn/post/7479625267029377051

#### process

##### Machine1

直接命令行即可安装完成 (不懂为啥自己电脑不行)

##### Machine2 — NLP project

1. python package 搜索 `xinference` 安装正常 (`pypi` 源)

   ```
   pip list | findstr xinference
   xinference                1.5.1
   ```

   

2. Terminal 报错如下 (详见 ./log/04_xinference_log.md—1)

   ```powershell
   pip install "xinference[all]"
   
   ...
   Collecting auto-gptq (from xinference[all])
     Using cached auto_gptq-0.7.1.tar.gz (126 kB)
     Preparing metadata (setup.py) ... error
     error: subprocess-exited-with-error
   
     × python setup.py egg_info did not run successfully.
     │ exit code: 1
     ╰─> [7 lines of output]
         Traceback (most recent call last):
           File "<string>", line 2, in <module>
           File "<pip-setuptools-caller>", line 34, in <module>
           File "C:\Users\%username%\AppData\Local\Temp\pip-install-nan3y5kn\auto-gptq_3e76e22d8e994083a5071a68b84a15cc\setup.py", line 62, in <module> 
             CUDA_VERSION = "".join(os.environ.get("CUDA_VERSION", default_cuda_version).split("."))
                                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
         AttributeError: 'NoneType' object has no attribute 'split'
         [end of output]
   
     note: This error originates from a subprocess, and is likely not a problem with pip.
   
   [notice] A new release of pip is available: 24.2 -> 25.1.1
   [notice] To update, run: python.exe -m pip install --upgrade pip
   error: metadata-generation-failed
   
   × Encountered error while generating package metadata.
   ╰─> See above for output.
   
   note: This is an issue with the package mentioned above, not pip.
   hint: See above for details.
   
   ```

   > 1. 官方 issue
   >    https://github.com/xorbitsai/inference/issues/1454
   >    只有 mac (已修复)，win10 未修复、未回复
   > 2. 搜索结果
   >    未测试 https://blog.csdn.net/naicha2/article/details/143965284

##### RTX 3080*2 1

```

```

###### ERROR

solution

```
pip install "cmake<4.0" cython numpy
pip install pyopenjtalk --no-build-isolation --no-cache-dir
```

```
root@autodl-container-xxxxxxxx:~# pip install "cmake<4.0" cython numpy
...
(详见 ./04_xinference_log.md—2)
...
Successfully built pyopenjtalk
Installing collected packages: pyopenjtalk
Successfully installed pyopenjtalk-0.3.4
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
```



> https://github.com/r9y9/pyopenjtalk/issues/99
>



###### ERROR 2

```

```

```
Successfully installed accelerate-1.7.0 aiofiles-24.1.0 aiohappyeyeballs-2.6.1 aiohttp-3.12.0 
...
(详见 ./log/04_xinference_log.md—3)
...
```

> https://github.com/xorbitsai/inference/issues/3111
>
> 社区版好像只能装vLLM、SGLang引擎

##### RES

```
root@autodl-container-xxxxxxxx:~# pip list
Package                        Version
------------------------------ --------------
absl-py                        2.1.0
...
(详见 ./log/04_xinference_log.md—4)
...
```





#### startup

1. 启动 xinference

   **DG**

   ```powershell
   (.dify_venv) PS D:\A_Project\1_dify> xinference-local --host 127.0.0.1 --port 9997
   2025-04-08 15:59:58,876 xinference.core.supervisor 25420 INFO     Xinference supervisor 127.0.0.1:36337 started
   2025-04-08 15:59:58,911 xinference.core.worker 25420 INFO     Starting metrics export server at 127.0.0.1:None
   2025-04-08 15:59:58,913 xinference.core.worker 25420 INFO     Checking metrics export server...
   2025-04-08 16:00:07,771 xinference.core.worker 25420 INFO     Metrics server is started at: http://127.0.0.1:51695
   2025-04-08 16:00:07,772 xinference.core.worker 25420 INFO     Purge cache directory: C:\Users\Digital\.xinference\cache
   2025-04-08 16:00:07,773 xinference.core.worker 25420 INFO     Connected to supervisor as a fresh worker
   2025-04-08 16:00:07,785 xinference.core.worker 25420 INFO     Xinference worker 127.0.0.1:36337 started
   2025-04-08 16:00:09,583 xinference.api.restful_api 18996 INFO     Starting Xinference at endpoint: http://127.0.0.1:9997
   2025-04-08 16:00:09,674 uvicorn.error 18996 INFO     Uvicorn running on http://127.0.0.1:9997 (Press CTRL+C to quit)
   ```

   

   **HW**

   ```powershell
   (venv) PS D:\path\to\project> xinference-local --host 127.0.0.1 --port 9997
   TensorFlow found but with version 1.14.0. Transformers requires version 2 minimum.
   2025-05-07 00:24:53,638 xinference.core.supervisor 17916 INFO     Xinference supervisor 127.0.0.1:19359 started
   2025-05-07 00:24:53,666 xinference.core.worker 17916 INFO     Starting metrics export server at 127.0.0.1:None
   2025-05-07 00:24:53,668 xinference.core.worker 17916 INFO     Checking metrics export server...
   2025-05-07 00:25:00,155 xinference.core.worker 17916 INFO     Metrics server is started at: http://127.0.0.1:46912
   2025-05-07 00:25:00,156 xinference.core.worker 17916 INFO     Purge cache directory: C:\Users\%username%\.xinference\cache
   2025-05-07 00:25:00,156 xinference.core.worker 17916 INFO     Connected to supervisor as a fresh worker
   2025-05-07 00:25:00,178 xinference.core.worker 17916 INFO     Xinference worker 127.0.0.1:19359 started
   2025-05-07 00:25:03,566 xinference.api.restful_api 11496 INFO     Starting Xinference at endpoint: http://127.0.0.1:9997
   2025-05-07 00:25:03,690 uvicorn.error 11496 INFO     Uvicorn running on http://127.0.0.1:9997 (Press CTRL+C to quit)
   ```

   > Thank for goddess! 好歹也是启动了

   

2. 浏览器打开 [Xinference](http://localhost:9997/ui/#/launch_model/llm)

   - http://localhost: 9997
   - http://localhost: 9997/ui/#/launch_model/llm

3. 下载模型

   ```powershell
   xinference launch --model-name qwen2.5 --model-type LLM --model-engine Transformers --model-format pytorch --size-in-billions 1_5 --quantization none --n-gpu auto --replica 1 --n-worker 1
   ```


> reference
>
> - [Xinference 本地直接安装、打开、部署、测试模型、api 调用_xinference 本地部署-CSDN 博客](https://blog.csdn.net/Zlzxzw/article/details/144622381)
> - [240713-Xinference 模型下载、管理及测试_xinference 下载模型-CSDN 博客](https://blog.csdn.net/qq_33039859/article/details/140396941)
> - [本地如何使用 docker 部署和使用 Xinference_xinference docker 部署-CSDN 博客](https://blog.csdn.net/jsyzliuyu/article/details/145831288)



### Bugs

#### 1. 503 xinference 模型下载失败 

```powershell
// commandline
RuntimeError: Failed to download model 'qwen2.5' (size: 1_5, format: pytorch) after multiple retries
2025-04-08 16:42:04,499 xinference.api.restful_api 18996 ERROR    [address=127.0.0.1:36337, pid=25420] Failed to download model 'qwen2.5' (size: 1_5, format: pytorch) after multiple retries
urllib3.exceptions.MaxRetryError: None: Max retries exceeded with url: https://www.modelscope.cn/api/v1/models/qwen/Qwen2.5-1.5B/repo?Revision=master&FilePath=generation_config.json (Caused by None)

// website
Server error: 503 - [address=127.0.0.1:36337, pid=25420] Failed to download model 'qwen2.5' (size: 1_5, format: pytorch) after multiple retries
```



> [在本地运行命令 xinference-local 启动 Xinference 修改存储路径-CSDN 博客](https://blog.csdn.net/greatsheep/article/details/141167266)
>
> [Xinference Huggingface 常用命令指定 Xinference 下载模型的路径 1. 通过环境变量全局设置 - 掘金](https://juejin.cn/post/7479625267029377051)







#### 2. pip install “xinference[all]” error

目前社区版只支持 [vllm] & []

```python
pip install "xinference[vllm]"
```







#### 3. vllm 引擎部署推理模型 TongGu

> 自定义模型参考文档
>
> https://inference.readthedocs.io/zh-cn/v1.6.0.post1/models/custom.html#

##### 1. 定义

```json
{
  "version": 1,
  "context_length": 2048,
  "model_name": "TongGu",
  "model_lang": [
    "zh"
  ],
  "model_ability": [
    "generate"
  ],
  "model_family": "baichuan-2-base",
  "model_specs": [
    {
      "model_format": "pytorch",
      "model_size_in_billions": 7,
      "quantizations": [
        "none"
      ],
      "model_id": "SCUT-DLVCLab/TongGu-7B-Instruct",
      "model_uri": "/root/autodl-tmp/models/TongGu"
    }
  ],
  "chat_template": """
    {%- if messages[0]['role'] == 'system' -%}
        {%- set system_message = messages[0]['content'] -%}
        {%- set messages = messages[1:] -%}
    {%- else -%}
        {% set system_message = '' -%}
    {%- endif -%}

    {{ bos_token + system_message }}
    {%- for message in messages -%}
        {%- if (message['role'] == 'user') != (loop.index0 % 2 == 0) -%}
            {{ raise_exception('Conversation roles must alternate user/assistant/user/assistant/...') }}
        {%- endif -%}

        {%- if message['role'] == 'user' -%}
            {{ 'USER: ' + message['content'] + '\n' }}
        {%- elif message['role'] == 'assistant' -%}
            {{ 'ASSISTANT: ' + message['content'] + eos_token + '\n' }}
        {%- endif -%}
    {%- endfor -%}

    {%- if add_generation_prompt -%}
        {{ 'ASSISTANT:' }}
    {% endif %}
    """,

}

```

```json
{
    "version": 1,
    "model_name": "TongGu",
    "model_description": "This is a custom model description.",
    "context_length": 2048,
    "model_lang": [
        "zh"
    ],
    "model_ability": [
        "chat"
    ],
    "model_specs": [
        {
            "model_uri": "/root/autodl-tmp/models/TongGu",
            "model_size_in_billions": 7,
            "model_format": "pytorch",
            "quantizations": [
                "none"
            ]
        }
    ],
    "model_family": "baichuan-2-chat",
    "chat_template": "{{ (messages|selectattr('role', 'equalto', 'system')|list|last).content|trim if (messages|selectattr('role', 'equalto', 'system')|list) else '' }}\n\n{% for message in messages %}\n{% if message['role'] == 'user' %}\n<reserved_106>\n{{ message['content']|trim -}}\n{% if not loop.last %}\n\n\n{% endif %}\n{% elif message['role'] == 'assistant' %}\n<reserved_107>\n{{ message['content']|trim -}}\n{% if not loop.last %}\n\n\n{% endif %}\n{% endif %}\n{% endfor %}\n{% if add_generation_prompt and messages[-1]['role'] != 'assistant' %}\n<reserved_107>\n{% endif %}",
    "stop_token_ids": [
        2,
        195
    ],
    "stop": []
}
```




##### 2. 注册

```bash
xinference register --model-type LLM --file /root/autodl-tmp/models/TongGu/TongGu.json --persist
```

如果报错则是未启动xinference, 需要先启动

```bash
xinference-local --host 0.0.0.0 --port 9997
```

##### 3. 查看

```bash
xinference registrations --model-type LLM
```

```
Type    Name            Language    				Ability            Is-built-in
------  -------------   --------------------------- -----------------  -------------
LLM     TongGu			['zh']                      ['generate']       False
```



##### 4. 启动

```bash
xinference launch --model-name TongGu --model-format pytorch --model-engine vllm
xinference launch --model-name TongGu --model-format pytorch --model-engine transformers
```

```python
Launch model name: TongGu with kwargs: {}
Launching model: 100%|███████████████████████████████████████████████████████████████████████████████████████████████ | 100.0%
Model uid: TongGu
```

###### 服务端报错

```bash
2025-05-28 12:33:16,916 xinference.core.worker 2363 INFO     [request e0092952-3b7c-11f0-b670-0242ac110004] Enter launch_builtin_model, args: <xinference.core.worker.WorkerActor object at 0x7fe540b04fe0>, kwargs: model_uid=TongGu-0,model_name=TongGu,model_size_in_billions=None,model_format=pytorch,quantization=None,model_engine=vllm,model_type=LLM,n_gpu=auto,request_limits=None,peft_model_config=None,gpu_idx=None,download_hub=None,model_path=None,xavier_config=None,trust_remote_code=True
2025-05-28 12:33:18,164 xinference.core.worker 2363 ERROR    Failed to load model TongGu-0
...
(详见 ./log/04_xinference_log.md—5)
...
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/llm_family.py", line 1207, in check_engine_by_spec_parameters
    raise ValueError(f"Model {model_name} cannot be run on engine {model_engine}.")
ValueError: Model TongGu cannot be run on engine vllm.
Task exception was never retrieved
future: <Task finished name='Task-861' coro=<SupervisorActor.launch_builtin_model.<locals>._launch_model() done, defined at /root/miniconda3/lib/python3.10/site-packages/xinference/core/supervisor.py:1109> exception=ValueError()>
...
(详见 ./04_xinference_log.md—5)
...
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/llm_family.py", line 1207, in check_engine_by_spec_parameters
    raise ValueError(f"Model {model_name} cannot be run on engine {model_engine}.")
ValueError: [address=0.0.0.0:25064, pid=2363] Model TongGu cannot be run on engine vllm.
```

换成 transformers

```bash
025-05-28 15:31:28,749 xinference.model.llm.llm_family 6276 WARNING  Remove the cache of user-defined model TongGu. Cache directory: /root/.xinference/cache/TongGu-pytorch-7b
2025-05-28 15:32:07,877 xinference.core.worker 6276 INFO     [request dc2fdaec-3b95-11f0-9d6a-0242ac110005] Enter launch_builtin_model, args: <xinference.core.worker.WorkerActor object at 0x7f88d78647c0>, kwargs: model_uid=TongGu-0,model_name=TongGu,model_size_in_billions=None,model_format=pytorch,quantization=None,model_engine=transformers,model_type=LLM,n_gpu=auto,request_limits=None,peft_model_config=None,gpu_idx=None,download_hub=None,model_path=None,xavier_config=None,trust_remote_code=True
2025-05-28 15:32:08,516 xinference.model.llm.llm_family 6276 INFO     Caching from URI: /root/autodl-tmp/models/TongGu
...
(详见 ./04_xinference_log.md—6)
...
```

查看

```bash
xinference list
UID     Type    Name    Format      Size (in billions)  Quantization
------  ------  ------  --------  --------------------  --------------
TongGu  LLM     TongGu  pytorch                      7  none
```





##### 5. 使用

```python
from xinference.client import Client

# replace with real xinference endpoint
endpoint = 'http://localhost:9997'
client = Client(endpoint)

# uid = client.launch_model(model_name='custom-llama-2', model_format='pytorch')

model = client.get_model(model_uid="TongGu")
model.generate(
    "将以下古文翻译为现代汉语：\n「昔我往矣，杨柳依依」",
    max_tokens=256,
    temperature=0.3
)
print(completion)
```



##### 6. 停止

```bash
xinference terminate --model-uid "TongGu" --endpoint "http://0.0.0.0:9997"
```

server terminal

```bash
2025-05-28 15:42:38,025 xinference.core.worker 6276 INFO     [request 53c8c310-3b97-11f0-9d6a-0242ac110005] Enter terminate_model, args: <xinference.core.worker.WorkerActor object at 0x7f88d78647c0>, kwargs: model_uid=TongGu-0
2025-05-28 15:42:38,972 xinference.core.worker 6276 INFO     [request 53c8c310-3b97-11f0-9d6a-0242ac110005] Leave terminate_model, elapsed time: 0 s
```



##### 7. 注销

```bash
xinference unregister --model-type LLM --model-name TongGu
```







#### 4. qwen3-8b 启动问题 (max seq len)

本地模型启动报错

```bash
ValueError: The model’s max seq len (32768) is larger than the maximum number of tokens that can be stored in KV cache (1152). Try increasing gpu_memory_utilization or decreasing max_model_len when initializing the engine.
```

##### solution

启动时设置 vllm 参数

```bash
max_model_len=6000 (<= 报错信息里的值即可)
```

> https://blog.csdn.net/h1773655323/article/details/138154900
>
> [未试验] https://blog.csdn.net/qq_38463737/article/details/139241176



#### 5. 运行报警 (gpu_memory_utilization)

跑 TongGu 的时候 xinference 服务端会出现如下的提示信息

```bash
WARNING 06-23 14:33:09 [scheduler.py:1800] Sequence group eb1c91ce-4ffb-11f0-b0ac-0242ac110008 is preempted by PreemptionMode.RECOMPUTE mode because there is not enough KV cache space. This can affect the end-to-end performance. Increase gpu_memory_utilization or tensor_parallel_size to provide more KV cache memory. total_num_cumulative_preemption=3501
```

##### solution

```python
from vllm import LLM
llm = LLM(
    model_name_or_path,
    tensor_parallel_size=2, 
    gpu_memory_utilization=0.95,
    max_model_len=2048,
    max_num_seqs=1024
)
```

相关参数说明

```
xinference launch --model-name TongGu --model-type LLM --model-engine vLLM --model-format pytorch --size-in-billions 7 --quantization none --n-gpu auto --replica 1 --n-worker 1 --model-path /root/autodl-tmp/models/TongGu
```

- gpu_memory_utilization

  vllm 会预先分配显存，默认值是 0.9，这和输入的 batch size 大小无关。

  gpu_memory_utilization 设置越大，可占用显存越大，就有更多显存可用于 KV 缓存，推理速度也会越快。在显存足够的情况下，gpu_memory_utilization 可以设置为 0.95。

- max_num_seqs

  一次推理最多能处理的 sequences 数量，默认值是 256。

  max_num_seqs 越大，能处理的请求数量就会越大，但提升也会有上限，不一定是越大越好：

  - 在 2 卡上，max_num_seqs 设置为 1024，相较于 256，速度提升 19%。
  - 在 4 卡上，max_num_seqs 设置为 2048，相较于 256，速度提升 35%；max_num_seqs 设置为 4096，相较于 256，速度提升 33%。

- max_model_len

  模型的最大生成长度，包含 prompt 长度和 generated 长度。这个值需要根据实际情况输入

- max_num_batched_tokens

  一次推理最多能处理的 tokens 数量，默认值是 2048

  max_num_batched_tokens 越大，能处理的 tokens 数量也就越大，但 vllm 内部会根据 max_model_len 自动计算 max_num_batched_tokens，所以可以不设置这个值。

- tensor_parallel_size

  张量并行时需要使用的 GPU 数量，使用多个 GPU 推理时，每个 GPU 都有更多的内存可用于 KV 缓存，能处理的请求数量更多，速度也会更快。

```json
{
    'gpu_memory_utilization': 0.95, 
    'tokenizer_mode': 'auto', 
    'trust_remote_code': True, 
    'tensor_parallel_size': 1, 
    'pipeline_parallel_size': 1, 
    'block_size': 16, 
    'swap_space': 4, 
    'max_num_seqs': 256, 
    'quantization': None, 
    'max_model_len': None, 
    'guided_decoding_backend': 'outlines', 
    'scheduling_policy': 'fcfs'
}
```

```
model_uid=TongGu-0, model_name=TongGu, model_size_in_billions=7, model_format=pytorch, quantization=none, model_engine=vLLM, model_type=LLM, n_gpu=auto, request_limits=None, peft_model_config=None, gpu_idx=None, download_hub=None, model_path=/root/autodl-tmp/models/TongGu, xavier_config=None, gpu_memory_utilization=0.95, max_num_seqs=512
```















## LLaMA-Factory

官方文档 https://llamafactory.readthedocs.io/zh-cn/latest/

### installation

1. 从源码安装到指定位置 (将所有文件存放在该路径下)

   ```powershell
   git clone --depth 1 https://github.com/hiyouga/LLaMA-Factory.git /root/LLaMA-Factory
   ```

   `--depth 1`: 浅克隆（仅克隆最近的提交）

2. 安装其他包

   ```powershell
   cd LLaMA-Factory
   pip install -e ".[torch,metrics]" --no-build-isolation
   ```

3. 查看安装版本

   由于当前为无卡模式，因此会有报警信息

   ```powershell
   (base) root@%username%:~/LLaMA-Factory/data# llamafactory-cli version
   INFO 07-19 11:00:58 [__init__.py:247] No platform detected, vLLM is running on UnspecifiedPlatform
   ----------------------------------------------------------
   | Welcome to LLaMA Factory, version 0.9.4.dev0           |
   |                                                        |
   | Project page: https://github.com/hiyouga/LLaMA-Factory |
   ----------------------------------------------------------
   ```

   ```
   (base) root@%username%:~/LLaMA-Factory/data# pip list | grep llamafactory
   llamafactory                             0.9.4.dev0         /root/LLaMA-Factory
   ```
   



### train

#### error

##### 1 缺少 deepspeed

详细内容见`./log/04_llama_Factory_log.md --- 4`

```python
ImportError: DeepSpeed is not available => install it using `pip3 install deepspeed`
```

###### solution

att. 需使用如下命令安装否则出现版本不匹配错误

```python
pip install "deepspeed<=0.16.9"
```

版本不匹配 (详细内容见`./log/04_llama_Factory_log.md --- 5`)

```bash
[rank0]: ImportError: deepspeed>=0.10.0,<=0.16.9 is required for a normal functioning of this module, but found deepspeed==0.17.2.
[rank0]: To fix: run `pip install deepspeed>=0.10.0,<=0.16.9`.
```



### References

> [使用LLaMA Factory微调LlaMA 3模型](https://help.aliyun.com/zh/pai/use-cases/fine-tune-a-llama-3-model-with-llama-factory)





## Ollama

### Ollama 本地部署 Qwen

Ollama 中文文档

https://ollama.readthedocs.io/

#### check current system version

```bash
cat /etc/issue
Ubuntu 20.04.4 LTS \n \l
```



### Linux

1. install ufw

   ```bash
   sudo apt-get update
   sudo apt-get install ufw
   ```

2. check ufw version

   ```bash
   ufw --version
       ufw 0.36
       Copyright 2008-2015 Canonical Ltd.
   ```

3. 

   ```bash
   sudo ufw allow 11434/tcp
   ```

4. 

   ```bash
   sudo apt update && sudo apt upgrade
   sudo apt install curl
   curl --version
   ```

```bash
(base) root@autodl-xxxxx:~# curl --version
curl 7.68.0 (x86_64-pc-linux-gnu) libcurl/7.68.0 OpenSSL/1.1.1f zlib/1.2.11 brotli/1.0.7 libidn2/2.2.0 libpsl/0.21.0 (+libidn2/2.2.0) libssh/0.9.3/openssl/zlib nghttp2/1.40.0 librtmp/2.3
Release-Date: 2020-01-08
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp 
Features: AsynchDNS brotli GSS-API HTTP2 HTTPS-proxy IDN IPv6 Kerberos Largefile libz NTLM NTLM_WB PSL SPNEGO SSL TLS-SRP UnixSockets
```

#### error

##### 1. 403 port

```bash
curl -fsSL https://ollama.com/install.sh | sh
>>> Installing ollama to /usr/local
>>> Downloading Linux amd64 bundle
curl: (28) Failed to connect to github.com port 443: Connection timed out                             #      #    #    #    


gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```

solution (**useless**)

```bash
git config --global http.proxy http://127.0.0.1:33210
git config --global https.proxy https://127.0.0.1:33210
#取消全局代理
git config --global --unset http.proxy
git config --global --unset https.proxy
```

##### 2. slow to download

reference：[linux 下载 ollama 缓慢](https://blog.csdn.net/ZXF_H/article/details/145699393?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-145699393-blog-145473247.235%5Ev43%5Econtrol&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-145699393-blog-145473247.235%5Ev43%5Econtrol&utm_relevant_index=9)

- 下载安装脚本到 Linux 本地

  ```bash
  curl -fsSL https://ollama.com/install.sh -o ollama_install.sh
  ```

- 使用 github 文件加速替换 github 下载地址

  ```bash
  sed -i 's|https://ollama.com/download/ollama-linux|https://gh.llkk.cc/https://github.com/ollama/ollama/releases/download/v0.5.7/ollama-linux|g' ollama_install.sh
  ```

- 替换后增加可执行权限

  ```bash
  chmod +x ollama_install.sh
  ```

- 执行 sh 下载安装

  ```bash
  sh ollama_install.sh
  ```

##### 3. 无法下载模型

```bash
WARNING: systemd is not running
WARNING: Unable to detect NVIDIA/AMD GPU. Install lspci or lshw to automatically detect and install GPU dependencies.
```

重新运行下载指令

```bash
ollama run qwen2.5:14b
```

##### 4. 修改模型路径

```bash
sudo mkdir -p /root/autodl-tmp/data/ollama/models
sudo chown -R root:root /root/autodl-tmp/data/ollama/models
sudo chmod -R 777 /root/autodl-tmp/data/ollama/models
```



#### 手动安装

下载并解压包：

```
curl -L https://ollama.com/download/ollama-linux-amd64.tgz -o ollama-linux-amd64.tgz
sudo tar -C /usr -xzf ollama-linux-amd64.tgz
```

```
curl -L https://ollama.com/download/ollama-linux-amd64.tgz -o ~/autodl-tmp/data/ollama/ollama-linux-amd64.tgz
sudo tar -C /usr -xzf ~/autodl-tmp/data/ollama/ollama-linux-amd64.tgz
```

```bash
root@autodl-xxxxx:~/autodl-tmp/data# sudo tar -C /usr -xzf ~/autodl-tmp/data/ollama/ollama-linux-amd64.tgz
root@autodl-xxxxx:~/autodl-tmp/data# ollama serve
Couldn't find '/root/.ollama/id_ed25519'. Generating new private key.
Your new public key is: 

ssh-ed25519 xxx/xxx

...
(详见 ./log/04_xinference_log.md—7)
...
```



#### start ollama

```
ollama serve
```



#### check start 

```
(base) root@autodl-xxxxx:~# ollama -v
ollama version is 0.5.7
```



#### download model

##### qwen: 7b

```bash
(base) root@autodl-xxxxx:~# ollama run qwen:7b
pulling manifest 
pulling 87f26aae09c7... 100% ▕██████████████████████████████████████████████████████████████▏ 4.5 GB
pulling 7c7b8e244f6a... 100% ▕██████████████████████████████████████████████████████████████▏ 6.9 KB
pulling 1da0581fd4ce... 100% ▕██████████████████████████████████████████████████████████████▏  130 B
pulling f02dd72bb242... 100% ▕██████████████████████████████████████████████████████████████▏   59 B
pulling c0312cf22ef0... 100% ▕██████████████████████████████████████████████████████████████▏  483 B
verifying sha256 digest 
writing manifest 
success
```

delete

```bash
ollama rm qwen:7b
deleted 'qwen:7b'
```



#### qwen2.5:14b

```bash
ollama run qwen2.5:14b
```

```bash
ollama list
NAME           ID              SIZE      MODIFIED      
qwen2.5:14b    7cdf5a0187d5    9.0 GB    9 minutes ago
```





### Windows

#### installation

需要提前创建子文件夹 `Ollama`

```powershell
OllamaSetup.exe /DIR="d:\some\location"
OllamaSetup.exe /DIR="d:\A_APP\Ollama"
```

```powershell
C:\Users\%username%>ollama -v
ollama version is 0.5.7

C:\Users\%username%>ollama run deepseek-r1:1.5b
pulling manifest
pulling aabd4debf0c8...  63% ▕██████████████████████              ▏ 709 MB/1.1 GB  305 KB/s  22m16s^C
C:\Users\%username%>ollama run deepseek-r1:1.5b
pulling manifest
pulling aabd4debf0c8...  80% ▕████████████████████████████        ▏ 890 MB/1.1 GB  729 KB/s   5m10s^C
C:\Users\%username%>ollama run deepseek-r1:1.5b
pulling manifest
pulling aabd4debf0c8... 100% ▕████████████████████████████████████▏ 1.1 GB
pulling 369ca498f347... 100% ▕████████████████████████████████████▏  387 B
pulling 6e4c38e1172f... 100% ▕████████████████████████████████████▏ 1.1 KB
pulling f4d24e9138dd... 100% ▕████████████████████████████████████▏  148 B
pulling a85fe2a2e58e... 100% ▕████████████████████████████████████▏  487 B
verifying sha256 digest
writing manifest
success
>>> /?
```



将 C:\Users\你的用户名\AppData\Local\Programs\Ollama 这个文件夹移动到 D 盘, 这里改为 D:\Ollama
修改用户变量的 PATH 变量, 方便系统识别, 将原来的 C:\Users\XX\AppData\Local\Programs\Ollama 路径更新为新的位置, 即 D:\Ollama
在系统变量中新建一个名为 OLLAMA_MODELS 的变量, 设置其值为模型文件的新位置, 例如 D:\Ollama\models



#### 1. useful cmd

- `netstat -aon | findstr 11434`：查找占用端口的进程。
- `tasklist | findstr "6892"`：查看该进程的详细信息。
- `taskkill /PID 6872 /F`：杀死该进程。

#### 2. 11434

Windows 中默认安装 Ollama 会开机启动。因此才会在 ollama serve 时报错如下：

```powershell
Error: listen tcp 127.0.0.1:11434: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.
```

##### 解决方法：

快捷键 win+x 打开任务管理器：启动应用中禁用掉 ollama，并在进程中结束 ollama 的任务。
再次尝试 ollama serve

##### 解决过程：

快捷键按下 win+r 键，输入 cmd，打开命令行终端。
输入 netstat -aon|findstr 11434 查看 11434 这个端口是否被占用。

```powershell
C:\Users\%username%>netstat -aon|findstr 11434
  TCP    127.0.0.1:11434        0.0.0.0:0              LISTENING       14448
```

上面的结果显示 11434 端口被占用 14448 进程占用，则用 tasklist 查看该进程运行的软件，发现 ollama 已经启动。

```powershell
C:\Users\%username%>tasklist|findstr "14448"
ollama.exe                   14448 Console                    4     22,052 K
```



> langchain 如何使用本地大模型（LLM）
>
> https://blog.csdn.net/chwei20002005/article/details/138159845
>
> langchain 和 Ollama 本地部署大语言模型
>
> https://blog.csdn.net/DuLNode/article/details/145098354
>









## Dify

[dify 的 2 种部署方式（源码/开发环境部署）](https://blog.csdn.net/spring_snow_/article/details/145878898)







# Bottom