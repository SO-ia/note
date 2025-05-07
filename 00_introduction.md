## Python

### download

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
   (base) root@autodl-container-19b1118252-be2efcfc:~/autodl-tmp/traditional# huggingface-cli download bert-base-chinese --local-dir /root/autodl-tmp/data/models --local-dir-use-symlinks False
   /root/miniconda3/lib/python3.8/site-packages/huggingface_hub/commands/download.py:139: FutureWarning: Ignoring --local-dir-use-symlinks. Downloading to a local directory does not use symlinks anymore.
     warnings.warn(
   Fetching 10 files:   0%|                                                      | 0/10 [00:00<?, ?it/s]Downloading 'model.safetensors' to '/root/autodl-tmp/data/models/.cache/huggingface/download/xGOKKLRSlIhH692hSVvI1-gpoa8=.3404a1ffd8da507042e8161013ba2a4fc49858b4e3f8fbf5ce5724f94883aec3.incomplete'
   Downloading 'tf_model.h5' to '/root/autodl-tmp/data/models/.cache/huggingface/download/a7eHxRFT3OeMBIFg52k2nfj5m7w=.612acd33db45677c3d6ba70615336619dc65cddf1ecf9d39a22dd1934af4aff2.incomplete'
   Downloading 'flax_model.msgpack' to '/root/autodl-tmp/data/models/.cache/huggingface/download/gPcsVCQDYDHk-_n0G9uADl7PXIM=.76df8425215fb9ede22e0393e356f82a99d84e79f078cd141afbbf9277460c8e.incomplete'
   Downloading '.gitattributes' to '/root/autodl-tmp/data/models/.cache/huggingface/download/wPaCkH-WbT7GsmxMKKrNZTV4nSM=.602b71f15d40ed68c5f96330e3f3175a76a32126.incomplete'
   Downloading 'README.md' to '/root/autodl-tmp/data/models/.cache/huggingface/download/Xn7B-BWUGOee2Y6hCZtEhtFu4BE=.048fdf63b2740ccf860ad1e5b4287ccbac89869a.incomplete'
   README.md: 1.85kB [00:00, 300kB/s]                                                                   
   Download complete. Moving file to /root/autodl-tmp/data/models/README.md   | 0.00/959 [00:00<?, ?B/s]
   Downloading 'pytorch_model.bin' to '/root/autodl-tmp/data/models/.cache/huggingface/download/Q1p2l2BzM1m6P5jKvr8WTq1TUio=.8a693db616eaf647ed2bfe531e1fa446637358fc108a8bf04e8d4db17e837ee9.incomplete'
   Downloading 'tokenizer_config.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/vzaExXFZNBay89bvlQv-ZcI6BTg=.2ba5de7675473164e07f3b3531748c9a6f113a2c.incomplete'
   Downloading 'config.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/8_PA_wEVGiVa2goH2H4KQOQpvVY=.a521dc2845bdddbe822864290c6b928396fc5ee8.incomplete'
   .gitattributes: 100%|███████████████████████████████████████████████| 445/445 [00:00<00:00, 80.6kB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/.gitattributes0.00/445 [00:00<?, ?B/s]
   Fetching 10 files:  10%|████▌                                         | 1/10 [00:01<00:09,  1.04s/it]Downloading 'tokenizer.json' to '/root/autodl-tmp/data/models/.cache/huggingface/download/HgM_lKo9sdSCfRtVg7MMFS7EKqo=.dd9401af0a4713df0e75066ae78d5bf6fa6c7116.incomplete'
   tokenizer_config.json: 100%|██████████████████████████████████████| 49.0/49.0 [00:00<00:00, 9.00kB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/tokenizer_config.jsonM [00:00<?, ?B/s]
   config.json: 624B [00:00, 113kB/s]                                                                   
   Download complete. Moving file to /root/autodl-tmp/data/models/config.json| 0.00/49.0 [00:00<?, ?B/s]
   Fetching 10 files:  30%|█████████████▊                                | 3/10 [00:01<00:02,  2.84it/s]Downloading 'vocab.txt' to '/root/autodl-tmp/data/models/.cache/huggingface/download/E2zehc7lrIVb8gRdx7qjK54iiZY=.ca4f9781030019ab9b253c6dcb8c7878b6dc87a5.incomplete'
   tokenizer.json: 269kB [00:00, 1.55MB/s]
   Download complete. Moving file to /root/autodl-tmp/data/models/tokenizer.json
   vocab.txt: 110kB [00:00, 670kB/s] 
   Download complete. Moving file to /root/autodl-tmp/data/models/vocab.txt  | 0.00/478M [00:00<?, ?B/s]
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

   



### packages

#### wandb

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

1. https://wandb.ai/authorize?ref=models
2. github 账号登录授权
   ![0](D:\A_assignment\work\assets\python\0.png)
3. 

> https://blog.csdn.net/weixin_53538865/article/details/136390750



#### Accelerator

```bash
TypeError: Accelerator.__init__() got an unexpected keyword argument 'dispatch_batches
```

##### solution

```bash
pip install accelerate==0.28.0
```





#### CRF

CRF 在 python 内有多个封装形式

##### 1. TorchCRF

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
TypeError                                 Traceback (most recent call last)
Input In [27], in <cell line: 15>()
     13         train_evaluate_loop(texts, labels, size, label_encoder)
     15 if __name__ == "__main__":
---> 16     main()

Input In [27], in main()
     10 for size in test_sizes:
     11 # for dataset_name in DATASET_CONFIG.keys():
     12     print(f"\n{'='*30} Testing with train/test split {1-size:.1f}/{size:.1f} {'='*30}")
---> 13     train_evaluate_loop(texts, labels, size, label_encoder)

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



##### 2. pytorch-crf

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











## Ollama

### Ollama 本地部署 Qwen

##### Ollama 中文文档

https://ollama.readthedocs.io/

##### check current system version

```bash
cat /etc/issue
Ubuntu 20.04.4 LTS \n \l
```



#### Linux

##### 1. install ufw

```bash
sudo apt-get update
sudo apt-get install ufw
```

##### 2. check ufw version

```bash
ufw --version
    ufw 0.36
    Copyright 2008-2015 Canonical Ltd.
```

##### 3. 

```bash
sudo ufw allow 11434/tcp
```

##### 4. 

```bash
sudo apt update && sudo apt upgrade
sudo apt install curl
curl --version
```

```bash
(base) root@autodl-container-19b1118252-be2efcfc:~# curl --version
curl 7.68.0 (x86_64-pc-linux-gnu) libcurl/7.68.0 OpenSSL/1.1.1f zlib/1.2.11 brotli/1.0.7 libidn2/2.2.0 libpsl/0.21.0 (+libidn2/2.2.0) libssh/0.9.3/openssl/zlib nghttp2/1.40.0 librtmp/2.3
Release-Date: 2020-01-08
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp 
Features: AsynchDNS brotli GSS-API HTTP2 HTTPS-proxy IDN IPv6 Kerberos Largefile libz NTLM NTLM_WB PSL SPNEGO SSL TLS-SRP UnixSockets
```

##### error

###### 1. 403 port

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

###### 2. slow to download

reference：[linux下载ollama缓慢](https://blog.csdn.net/ZXF_H/article/details/145699393?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-145699393-blog-145473247.235%5Ev43%5Econtrol&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-145699393-blog-145473247.235%5Ev43%5Econtrol&utm_relevant_index=9)

- 下载安装脚本到Linux本地

  ```bash
  curl -fsSL https://ollama.com/install.sh -o ollama_install.sh
  ```

-  使用github文件加速替换github下载地址

  ```bash
  sed -i 's|https://ollama.com/download/ollama-linux|https://gh.llkk.cc/https://github.com/ollama/ollama/releases/download/v0.5.7/ollama-linux|g' ollama_install.sh
  ```

- 替换后增加可执行权限

  ```bash
  chmod +x ollama_install.sh
  ```

- 执行sh下载安装

  ```bash
  sh ollama_install.sh
  ```

###### 3. 无法下载模型

```bash
WARNING: systemd is not running
WARNING: Unable to detect NVIDIA/AMD GPU. Install lspci or lshw to automatically detect and install GPU dependencies.
```

重新运行下载指令

```bash
ollama run qwen2.5:14b
```

###### 4. 修改模型路径

```bash
sudo mkdir -p /root/autodl-tmp/data/ollama/models
sudo chown -R root:root /root/autodl-tmp/data/ollama/models
sudo chmod -R 775 /root/autodl-tmp/data/ollama/models
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
root@autodl-container-19b1118252-be2efcfc:~/autodl-tmp/data# sudo tar -C /usr -xzf ~/autodl-tmp/data/ollama/ollama-linux-amd64.tgz
root@autodl-container-19b1118252-be2efcfc:~/autodl-tmp/data# ollama serve
Couldn't find '/root/.ollama/id_ed25519'. Generating new private key.
Your new public key is: 

ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEqIxov01DJnniyKRqBG8Bi/JIsx6uTSk5q3QqJY3iUu

2025/02/06 17:24:31 routes.go:1187: INFO server config env="map[CUDA_VISIBLE_DEVICES: GPU_DEVICE_ORDINAL: HIP_VISIBLE_DEVICES: HSA_OVERRIDE_GFX_VERSION: HTTPS_PROXY: HTTP_PROXY: NO_PROXY: OLLAMA_DEBUG:false OLLAMA_FLASH_ATTENTION:false OLLAMA_GPU_OVERHEAD:0 OLLAMA_HOST:http://127.0.0.1:11434 OLLAMA_INTEL_GPU:false OLLAMA_KEEP_ALIVE:5m0s OLLAMA_KV_CACHE_TYPE: OLLAMA_LLM_LIBRARY: OLLAMA_LOAD_TIMEOUT:5m0s OLLAMA_MAX_LOADED_MODELS:0 OLLAMA_MAX_QUEUE:512 OLLAMA_MODELS:/root/.ollama/models OLLAMA_MULTIUSER_CACHE:false OLLAMA_NOHISTORY:false OLLAMA_NOPRUNE:false OLLAMA_NUM_PARALLEL:0 OLLAMA_ORIGINS:[http://localhost https://localhost http://localhost:* https://localhost:* http://127.0.0.1 https://127.0.0.1 http://127.0.0.1:* https://127.0.0.1:* http://0.0.0.0 https://0.0.0.0 http://0.0.0.0:* https://0.0.0.0:* app://* file://* tauri://* vscode-webview://*] OLLAMA_SCHED_SPREAD:false ROCR_VISIBLE_DEVICES: http_proxy: https_proxy: no_proxy:]"
time=2025-02-06T17:24:31.389+08:00 level=INFO source=images.go:432 msg="total blobs: 0"
time=2025-02-06T17:24:31.390+08:00 level=INFO source=images.go:439 msg="total unused blobs removed: 0"
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] POST   /api/pull                 --> github.com/ollama/ollama/server.(*Server).PullHandler-fm (5 handlers)
[GIN-debug] POST   /api/generate             --> github.com/ollama/ollama/server.(*Server).GenerateHandler-fm (5 handlers)
[GIN-debug] POST   /api/chat                 --> github.com/ollama/ollama/server.(*Server).ChatHandler-fm (5 handlers)
[GIN-debug] POST   /api/embed                --> github.com/ollama/ollama/server.(*Server).EmbedHandler-fm (5 handlers)
[GIN-debug] POST   /api/embeddings           --> github.com/ollama/ollama/server.(*Server).EmbeddingsHandler-fm (5 handlers)
[GIN-debug] POST   /api/create               --> github.com/ollama/ollama/server.(*Server).CreateHandler-fm (5 handlers)
[GIN-debug] POST   /api/push                 --> github.com/ollama/ollama/server.(*Server).PushHandler-fm (5 handlers)
[GIN-debug] POST   /api/copy                 --> github.com/ollama/ollama/server.(*Server).CopyHandler-fm (5 handlers)
[GIN-debug] DELETE /api/delete               --> github.com/ollama/ollama/server.(*Server).DeleteHandler-fm (5 handlers)
[GIN-debug] POST   /api/show                 --> github.com/ollama/ollama/server.(*Server).ShowHandler-fm (5 handlers)
[GIN-debug] POST   /api/blobs/:digest        --> github.com/ollama/ollama/server.(*Server).CreateBlobHandler-fm (5 handlers)
[GIN-debug] HEAD   /api/blobs/:digest        --> github.com/ollama/ollama/server.(*Server).HeadBlobHandler-fm (5 handlers)
[GIN-debug] GET    /api/ps                   --> github.com/ollama/ollama/server.(*Server).PsHandler-fm (5 handlers)
[GIN-debug] POST   /v1/chat/completions      --> github.com/ollama/ollama/server.(*Server).ChatHandler-fm (6 handlers)
[GIN-debug] POST   /v1/completions           --> github.com/ollama/ollama/server.(*Server).GenerateHandler-fm (6 handlers)
[GIN-debug] POST   /v1/embeddings            --> github.com/ollama/ollama/server.(*Server).EmbedHandler-fm (6 handlers)
[GIN-debug] GET    /v1/models                --> github.com/ollama/ollama/server.(*Server).ListHandler-fm (6 handlers)
[GIN-debug] GET    /v1/models/:model         --> github.com/ollama/ollama/server.(*Server).ShowHandler-fm (6 handlers)
[GIN-debug] GET    /                         --> github.com/ollama/ollama/server.(*Server).GenerateRoutes.func1 (5 handlers)
[GIN-debug] GET    /api/tags                 --> github.com/ollama/ollama/server.(*Server).ListHandler-fm (5 handlers)
[GIN-debug] GET    /api/version              --> github.com/ollama/ollama/server.(*Server).GenerateRoutes.func2 (5 handlers)
[GIN-debug] HEAD   /                         --> github.com/ollama/ollama/server.(*Server).GenerateRoutes.func1 (5 handlers)
[GIN-debug] HEAD   /api/tags                 --> github.com/ollama/ollama/server.(*Server).ListHandler-fm (5 handlers)
[GIN-debug] HEAD   /api/version              --> github.com/ollama/ollama/server.(*Server).GenerateRoutes.func2 (5 handlers)
time=2025-02-06T17:24:31.390+08:00 level=INFO source=routes.go:1238 msg="Listening on 127.0.0.1:11434 (version 0.5.7)"
time=2025-02-06T17:24:31.391+08:00 level=INFO source=routes.go:1267 msg="Dynamic LLM libraries" runners="[cpu cpu_avx cpu_avx2 cuda_v11_avx cuda_v12_avx rocm_avx]"
time=2025-02-06T17:24:31.392+08:00 level=INFO source=gpu.go:226 msg="looking for compatible GPUs"
time=2025-02-06T17:24:31.407+08:00 level=INFO source=gpu.go:620 msg="no nvidia devices detected by library /usr/lib/x86_64-linux-gnu/libcuda.so.525.89.02"
time=2025-02-06T17:24:31.412+08:00 level=INFO source=gpu.go:630 msg="Unable to load cudart library /usr/lib/x86_64-linux-gnu/libcuda.so.465.19.01: symbol lookup for cuCtxCreate_v3 failed: /usr/lib/x86_64-linux-gnu/libcuda.so.465.19.01: undefined symbol: cuCtxCreate_v3"
time=2025-02-06T17:24:31.412+08:00 level=INFO source=gpu.go:630 msg="Unable to load cudart library /usr/lib/x86_64-linux-gnu/libcuda.so.510.60.02: Unable to load /usr/lib/x86_64-linux-gnu/libcuda.so.510.60.02 library to query for Nvidia GPUs: /usr/lib/x86_64-linux-gnu/libcuda.so.510.60.02: file too short"
time=2025-02-06T17:24:31.412+08:00 level=INFO source=gpu.go:630 msg="Unable to load cudart library /usr/lib/x86_64-linux-gnu/libcuda.so.515.65.01: Unable to load /usr/lib/x86_64-linux-gnu/libcuda.so.515.65.01 library to query for Nvidia GPUs: /usr/lib/x86_64-linux-gnu/libcuda.so.515.65.01: file too short"
time=2025-02-06T17:24:31.412+08:00 level=INFO source=gpu.go:630 msg="Unable to load cudart library /usr/lib/x86_64-linux-gnu/libcuda.so.515.76: Unable to load /usr/lib/x86_64-linux-gnu/libcuda.so.515.76 library to query for Nvidia GPUs: /usr/lib/x86_64-linux-gnu/libcuda.so.515.76: file too short"
time=2025-02-06T17:24:31.452+08:00 level=INFO source=gpu.go:392 msg="no compatible GPUs were discovered"
time=2025-02-06T17:24:31.453+08:00 level=INFO source=types.go:131 msg="inference compute" id=0 library=cpu variant=avx2 compute="" driver=0.0 name="" total="375.8 GiB" available="336.7 GiB"
```







#### start ollama

```
ollama serve
```



#### check start 

```
(base) root@autodl-container-19b1118252-be2efcfc:~# ollama -v
ollama version is 0.5.7
```



#### download

##### qwen:7b

```
(base) root@autodl-container-19b1118252-be2efcfc:~# ollama run qwen:7b
pulling manifest 
pulling 87f26aae09c7... 100% ▕██████████████████████████████████████████████████████████████▏ 4.5 GB
pulling 7c7b8e244f6a... 100% ▕██████████████████████████████████████████████████████████████▏ 6.9 KB
pulling 1da0581fd4ce... 100% ▕██████████████████████████████████████████████████████████████▏  130 B
pulling f02dd72bb242... 100% ▕██████████████████████████████████████████████████████████████▏   59 B
pulling c0312cf22ef0... 100% ▕██████████████████████████████████████████████████████████████▏  483 B
verifying sha256 digest 
writing manifest 
pulling manifest 
pulling 87f26aae09c7... 100% ▕██████████████████████████████████████████████████████████████▏ 4.5 GB
pulling 7c7b8e244f6a... 100% ▕██████████████████████████████████████████████████████████████▏ 6.9 KB
pulling 1da0581fd4ce... 100% ▕██████████████████████████████████████████████████████████████▏  130 B
pulling f02dd72bb242... 100% ▕██████████████████████████████████████████████████████████████▏   59 B
pulling c0312cf22ef0... 100% ▕██████████████████████████████████████████████████████████████▏  483 B
verifying sha256 digest 
writing manifest 
pulling manifest 
pulling 87f26aae09c7... 100% ▕██████████████████████████████████████████████████████████████▏ 4.5 GB
pulling 7c7b8e244f6a... 100% ▕██████████████████████████████████████████████████████████████▏ 6.9 KB
pulling 1da0581fd4ce... 100% ▕██████████████████████████████████████████████████████████████▏  130 B
pulling f02dd72bb242... 100% ▕██████████████████████████████████████████████████████████████▏   59 B
pulling c0312cf22ef0... 100% ▕██████████████████████████████████████████████████████████████▏  483 B
verifying sha256 digest 
writing manifest 
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

###### delete

```bash
ollama rm qwen:7b
deleted 'qwen:7b'
```



##### qwen2.5:14b

```bash
ollama run qwen2.5:14b
```

```bash
ollama list
NAME           ID              SIZE      MODIFIED      
qwen2.5:14b    7cdf5a0187d5    9.0 GB    9 minutes ago
```





### Windows

需要提前创建子文件夹 `Ollama`

```powershell
OllamaSetup.exe /DIR="d:\some\location"
OllamaSetup.exe /DIR="d:\A_APP\Ollama"
```

```powershell
C:\Users\HUAWEI>ollama -v
ollama version is 0.5.7

C:\Users\HUAWEI>ollama run deepseek-r1:1.5b
pulling manifest
pulling aabd4debf0c8...  63% ▕██████████████████████              ▏ 709 MB/1.1 GB  305 KB/s  22m16s^C
C:\Users\HUAWEI>ollama run deepseek-r1:1.5b
pulling manifest
pulling aabd4debf0c8...  80% ▕████████████████████████████        ▏ 890 MB/1.1 GB  729 KB/s   5m10s^C
C:\Users\HUAWEI>ollama run deepseek-r1:1.5b
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



将C:\Users\你的用户名\AppData\Local\Programs\Ollama这个文件夹移动到D盘,这里改为D:\Ollama
修改用户变量的PATH变量,方便系统识别,将原来的C:\Users\XX\AppData\Local\Programs\Ollama路径更新为新的位置,即D:\Ollama
在系统变量中新建一个名为OLLAMA_MODELS的变量,设置其值为模型文件的新位置,例如D:\Ollama\models



#### 1. useful cmd

- `netstat -aon | findstr 11434`：查找占用端口的进程。
- `tasklist | findstr "6892"`：查看该进程的详细信息。
- `taskkill /PID 6872 /F`：杀死该进程。

#### 2. 11434

Windows中默认安装Ollama会开机启动。因此才会在ollama serve时报错如下：

```powershell
Error: listen tcp 127.0.0.1:11434: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.
```

##### 解决方法：

快捷键win+x打开任务管理器：启动应用中禁用掉ollama，并在进程中结束ollama的任务。
再次尝试ollama serve

##### 解决过程：

快捷键按下win+r键，输入cmd，打开命令行终端。
输入netstat -aon|findstr 11434查看11434这个端口是否被占用。

```powershell
C:\Users\HUAWEI>netstat -aon|findstr 11434
  TCP    127.0.0.1:11434        0.0.0.0:0              LISTENING       14448
```

上面的结果显示 11434 端口被占用14448进程占用，则用 tasklist 查看该进程运行的软件，发现 ollama 已经启动。

```powershell
C:\Users\HUAWEI>tasklist|findstr "14448"
ollama.exe                   14448 Console                    4     22,052 K
```

#### 3.

langchain 如何使用本地大模型（LLM）

https://blog.csdn.net/chwei20002005/article/details/138159845

langchain和Ollama本地部署大语言模型

https://blog.csdn.net/DuLNode/article/details/145098354



## openai

https://python.langchain.com/



## langchain

https://zhuanlan.zhihu.com/p/656646499

langchain官方文档

eng

https://python.langchain.com/docs/introduction/

chinese

http://langchain.ichuangpai.com/

#### pydantic 报错

##### error

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

##### solution

检查pydantic版本

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



#### langchain-ollama 与 pydantic 不兼容

##### error

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

##### solution

```bash
# 安装指定版本（需验证与ollama的兼容性）
pip install "pydantic<2.0" "langchain-ollama==0.1.3"  # 选择已知兼容版本

# output
pip install "pydantic<2.0" "langchain-ollama==0.1.3"
Looking in indexes: https://repo.huaweicloud.com/repository/pypi/simple
Requirement already satisfied: pydantic<2.0 in /root/miniconda3/lib/python3.8/site-packages (1.10.13)
Requirement already satisfied: langchain-ollama==0.1.3 in /root/miniconda3/lib/python3.8/site-packages (0.1.3)
Requirement already satisfied: langchain-core<0.3.0,>=0.2.36 in /root/miniconda3/lib/python3.8/site-packages (from langchain-ollama==0.1.3) (0.2.43)
Requirement already satisfied: ollama<1,>=0.3.0 in /root/miniconda3/lib/python3.8/site-packages (from langchain-ollama==0.1.3) (0.4.7)
Requirement already satisfied: typing-extensions>=4.2.0 in /root/miniconda3/lib/python3.8/site-packages (from pydantic<2.0) (4.12.2)
Requirement already satisfied: PyYAML>=5.3 in /root/miniconda3/lib/python3.8/site-packages (from langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (6.0)
Requirement already satisfied: langsmith<0.2.0,>=0.1.112 in /root/miniconda3/lib/python3.8/site-packages (from langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (0.1.147)
Requirement already satisfied: jsonpatch<2.0,>=1.33 in /root/miniconda3/lib/python3.8/site-packages (from langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (1.33)
Requirement already satisfied: tenacity!=8.4.0,<9.0.0,>=8.1.0 in /root/miniconda3/lib/python3.8/site-packages (from langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (8.5.0)
Requirement already satisfied: packaging<25,>=23.2 in /root/miniconda3/lib/python3.8/site-packages (from langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (24.2)
Requirement already satisfied: jsonpointer>=1.9 in /root/miniconda3/lib/python3.8/site-packages (from jsonpatch<2.0,>=1.33->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (2.4)
Requirement already satisfied: httpx<1,>=0.23.0 in /root/miniconda3/lib/python3.8/site-packages (from langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (0.28.1)
Requirement already satisfied: requests-toolbelt<2.0.0,>=1.0.0 in /root/miniconda3/lib/python3.8/site-packages (from langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (1.0.0)
Requirement already satisfied: requests<3,>=2 in /root/miniconda3/lib/python3.8/site-packages (from langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (2.32.3)
Requirement already satisfied: orjson<4.0.0,>=3.9.14 in /root/miniconda3/lib/python3.8/site-packages (from langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (3.10.15)
Requirement already satisfied: httpcore==1.* in /root/miniconda3/lib/python3.8/site-packages (from httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (1.0.7)
Requirement already satisfied: idna in /root/miniconda3/lib/python3.8/site-packages (from httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (2.10)
Requirement already satisfied: anyio in /root/miniconda3/lib/python3.8/site-packages (from httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (3.6.1)
Requirement already satisfied: certifi in /root/miniconda3/lib/python3.8/site-packages (from httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (2023.11.17)
Requirement already satisfied: h11<0.15,>=0.13 in /root/miniconda3/lib/python3.8/site-packages (from httpcore==1.*->httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (0.14.0)
Collecting ollama<1,>=0.3.0
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/4a/60/ac0e47c4c400fbd1a72a3c6e4a76cf5ef859d60677e7c4b9f0203c5657d3/ollama-0.4.6-py3-none-any.whl (13 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/93/71/44e508b6be7cc12efc498217bf74f443dbc1a31b145c87421d20fe61b70b/ollama-0.4.5-py3-none-any.whl (13 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/d3/01/815774a30d0047d464add27e2824a5b1d02ea4ad021c83590cd753e5f511/ollama-0.4.4-py3-none-any.whl (13 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/1e/a9/3af6f408b0851aca56c6badd86af5364aa5635dd2e397a72999d522297a8/ollama-0.4.3-py3-none-any.whl (13 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/da/8e/b651790e301c555fe76869308f9c8af1014146ce4187291cf13eb8109096/ollama-0.4.2-py3-none-any.whl (13 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/bb/bd/77240baf373e4e04639d1a78a589dad2565cc80572cb8f1d56c8f6244f39/ollama-0.4.1-py3-none-any.whl (12 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/0e/aa/999aec53ce5b481abac7abbb507a86570cea5e7762c6dd42dba8ae84e0e1/ollama-0.4.0-py3-none-any.whl (12 kB)
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/6a/ca/d22905ac3f768523f778189d38c9c6cd9edf4fa9dd09cb5a3fc57b184f90/ollama-0.3.3-py3-none-any.whl (10 kB)
Collecting httpx<1,>=0.23.0
  Downloading https://repo.huaweicloud.com/repository/pypi/packages/56/95/9377bcb415797e44274b51d46e3249eba641711cf3348050f76ee7b15ffc/httpx-0.27.2-py3-none-any.whl (76 kB)
     |████████████████████████████████| 76 kB 4.8 MB/s 
Requirement already satisfied: sniffio in /root/miniconda3/lib/python3.8/site-packages (from httpx<1,>=0.23.0->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (1.2.0)
Requirement already satisfied: charset-normalizer<4,>=2 in /root/miniconda3/lib/python3.8/site-packages (from requests<3,>=2->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (2.1.1)
Requirement already satisfied: urllib3<3,>=1.21.1 in /root/miniconda3/lib/python3.8/site-packages (from requests<3,>=2->langsmith<0.2.0,>=0.1.112->langchain-core<0.3.0,>=0.2.36->langchain-ollama==0.1.3) (1.26.6)
Installing collected packages: httpx, ollama
  Attempting uninstall: httpx
    Found existing installation: httpx 0.28.1
    Uninstalling httpx-0.28.1:
      Successfully uninstalled httpx-0.28.1
  Attempting uninstall: ollama
    Found existing installation: ollama 0.4.7
    Uninstalling ollama-0.4.7:
      Successfully uninstalled ollama-0.4.7
Successfully installed httpx-0.27.2 ollama-0.3.3
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
```

###### before

```
pip list | grep langchain
langchain                      0.2.17
langchain-community            0.2.19
langchain-core                 0.2.43
langchain-ollama               0.1.3
langchain-text-splitters       0.2.4
```

###### after

```
pip list | grep langchain
langchain                      0.2.17
langchain-community            0.2.19
langchain-core                 0.2.43
langchain-ollama               0.1.3
langchain-text-splitters       0.2.4
```





## pycharm

#### 修改idea配置文件位置从C盘更改到D盘

[link](https://sgknight.blog.csdn.net/article/details/129013857?fromshare=blogdetail&sharetype=blogdetail&sharerId=129013857&sharerefer=PC&sharesource=qq_73921758&sharefrom=from_link)





## pip

#### cache

[link](https://blog.csdn.net/qyhua/article/details/139587214)

```
C:\Users\HUAWEI>pip cache dir
c:\users\huawei\appdata\local\pip\cache
```

##### 1. 清理pip的缓存

pip提供了清理缓存的简单命令。你可以通过以下命令删除所有的缓存文件：

```
pip cache purge
```

运行该命令后，pip将删除所有缓存文件。此操作不会影响已经安装的包，只是清除了pip用于加快安装速度的缓存文件。另外也可以手动删除缓存目录中的文件和文件夹。只需打开你在pip.ini中指定的缓存目录，选择所有文件并删除即可。

##### 2. 手动管理pip缓存

除了使用pip cache purge命令清理缓存外，pip还提供了更细粒度的缓存管理命令。你可以使用以下命令查看当前的缓存文件列表：

```
pip cache list
```

该命令会列出所有存储在缓存目录中的文件，方便你检查具体的缓存内容。

此外，如果只删除某些特定的缓存文件，而不是全部清除，可以使用 `pip cache remove` 命令。例如：

```
pip cache remove package_name
```

此命令会删除与指定包名相关的缓存文件，而保留其他缓存内容。

##### run at 2025/2/4 15:02

```
C:\Users\HUAWEI>pip cache purge
Files removed: 1335
```



## VSCode

route: **C:\Users\HUAWEI\AppData\Local\Microsoft\vscode-cpptools**

[link](https://www.52pojie.cn/forum.php?mod=viewthread&tid=1959079)

VsCode是一款**轻量级**代码编辑器

可用一段就会很快发现，“轻量级”的VsCode并不轻量

不统计不知道，一统计吓一跳，使用了一段时间后，VsCode占用了我C盘10G+的空间！

好家伙，于是我决定治理一下VsCode，让VsCode变得真正的轻量级。

#### VsCode的空间占用分析

VsCode所占用的空间，主要包括四大部分（下面是我写此博客时统计的结果）：

1. `程序的安装目录`：大约会占用350M
2. `%userprofile%\.vscode`：可达800M。主要为：各个拓展。VsCode卸载拓展似乎不会删除硬盘上的文件，因此这个里面很大，并且混有很多不用的
3. `%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch`：用一段时间能达到4G 与C(++)语言有关，关闭程序后可以直接删。不使用VsCode编辑C/C++的用户可能无此痛苦
4. `%userprofile%\AppData\Roaming\Code`：2G+ 存放用户数据、配置等。 （可以通过启动时添加--user-data-dir NewDir 来使其他目录作为配置）

可以定期删除的地方，有`3. ipch`（可完全删除） 和 `4. Romaing`（不可完全删除）

##### 4. Romaing中，到底哪些可以定期删除

对`%userprofile%\AppData\Roaming\Code`中的文件进行更进一步地分析，我得到了如下结论：

```css
%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs   用一段时间可以达到500M   可以直接删
%userprofile%\AppData\Roaming\Code\Cache       很快几十M
%userprofile%\AppData\Roaming\Code\CachedData  很快几十M
%userprofile%\AppData\Roaming\Code\CachedExtensions  安装新插件时，似乎默认不会自动删除，安装插件一多能达到800M
%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs 反正也是与插件有关的，也能达到几百M
%userprofile%\AppData\Roaming\Code\Code Cache    十几M
%userprofile%\AppData\Roaming\Code\Crashpad      十几M  用来存放崩溃信息
%userprofile%\AppData\Roaming\Code\logs          几十M  这个可以直接删，用来存放日志记录
%userprofile%\AppData\Roaming\Code\Service Worker 1G    
    %userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage   1G  主要位于这里
    %userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache    10M
%userprofile%\AppData\Roaming\Code\User          600M
    %userprofile%\AppData\Roaming\Code\User\workspaceStorage  500M  每打开一个工作目录就会在这个目录下生成一个文件夹
    %userprofile%\AppData\Roaming\Code\User\History           100M
            每Ctrl+S(仅限有修改的成功的重新保存)一次就会生成一个副本。
            这个不是按git的思路只存放更改，而是整个文件全部Copy一份。
            一个100多k的源码保存十次就是1M，对于习惯随手Ctrl+S的用户会占用较大的空间
            但是，删除之后将会影响历史版本的还原。
            其中，文件名采用了代码混淆技术，每个文件会生成一个文件夹，真正的文件名、各个文件对应文件保存时间都在每个文件夹下的entries.json中
    %userprofile%\AppData\Roaming\Code\User\snippets    这个不能删，并且重装还得记得备份（如果没有自动还原的话）这个是用户自定义的代码片段
```

#### 能定时删除的目录

1. `%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch`
2. `%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs`
3. `%userprofile%\AppData\Roaming\Code\Cache`
4. `%userprofile%\AppData\Roaming\Code\CachedData`
5. `%userprofile%\AppData\Roaming\Code\CachedExtensions`
6. `%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs`
7. `%userprofile%\AppData\Roaming\Code\Code Cache`
8. `%userprofile%\AppData\Roaming\Code\Crashpad`
9. `%userprofile%\AppData\Roaming\Code\logs`
10. `%userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage`
11. `%userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache`
12. `%userprofile%\AppData\Roaming\Code\User\workspaceStorage`
13. `%userprofile%\AppData\Roaming\Code\User\History`

这么多文件夹总不可能手动地一个一个地删除，因此我写了一个脚本：

```bash
 复制代码 隐藏代码@rem example:
@REM del "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/" /s /q /f
@REM rd "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/" /s /q
@REM md "%userprofile%/AppData/Local/Microsoft/vscode-cpptools/ipch/"

@echo off

call:EmptyOneDir "%userprofile%\AppData\Local\Microsoft\vscode-cpptools\ipch"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Cache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedData"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensions"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\CachedExtensionVSIXs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Code Cache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Crashpad"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\logs"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Service Worker\CacheStorage"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\Service Worker\ScriptCache"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\User\workspaceStorage"
call:EmptyOneDir "%userprofile%\AppData\Roaming\Code\User\History"

goto end

:EmptyOneDir  rem same as Let empty [path] /q
    echo empty %1
    echo del %1 /s /q /f
    del %1 /s /q /f
    echo rd %1 /s /q
    rd %1 /s /q
    echo md %1
    md %1
:end
```

**只需要将这个脚本另存为CleanVsCode.bat，并定期双击运行一次，就能定期释放大量空间**

当然，释放的空间直接取决于你的VsCode所产生的缓存大小，间接取决于你的VsCode的使用次数。

最好关闭VsCode后再运行脚本。

#### ⚠️Warning

运行脚本后再次运行VsCode基本上看不出什么不同，只是当前工作路径下所打开的文件需要重新手动点击打开。

毕竟是一个能删除很多东西的脚本，因此请谨慎使用。

我作为本篇博客的原创博主，只是为大家提供了一个便捷的方法，但是其可能造成的后果，博主并不承担责任。

但是大家可以放心的是，我自己也在定期运行这个脚本。

准备有空的时候将其加入Windows计划，以实现定期地自动释放空间。





## Maven (.m2)

https://ask.csdn.net/questions/7548212





## Google

### Browser

#### installation

1、创建D盘A_APP\Google文件夹：分别创建Chrome和PersonData文件夹
2、创建C盘Google文件夹:\Program Files\Google；Google文件夹里面为空
3、删除C盘Google文件夹::\Program Files (x86)\Google
4、管理员模式运行cmd
5、创建软连接

```powershell
mklink /d  "C:\Program Files\Google\Chrome"  "D:\A_APP\Google\Chrome"
mklink /d  "C:\Program Files (x86)\Google"  "D:\A_APP\Google"
mklink /d  "C:\Users\HUAWEI\AppData\Local\Google" "D:\A_APP\Google\PersonData"
```

6、安装chrome

6、安装chrome

 命令如下 

```powershell
C:\Windows\System32>mklink /d  "C:\Program Files\Google\Chrome"  "D:\A_APP\Google\Chrome"
为 C:\Program Files\Google\Chrome <<===>> D:\A_APP\Google\Chrome 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Program Files (x86)\Google"  "D:\A_APP\Google"
为 C:\Program Files (x86)\Google <<===>> D:\A_APP\Google 创建的符号链接

C:\Windows\System32>mklink /d  "C:\Users\HUAWEI\AppData\Local\Google" "D:\A_APP\Google\PersonData"
为 C:\Users\HUAWEI\AppData\Local\Google <<===>> D:\A_APP\Google\PersonData 创建的 符号链接
```



#### disable update

`trying ……`

```powershell
修改文件夹名称
D:\A_APP\Google\GoogleUpdater.disabled
D:\A_APP\Google\Update.disabled
```

> references
>
> https://stackoverflow.com/questions/18483087/how-to-disable-google-chrome-auto-update





# Bottom