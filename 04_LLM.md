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

#### process

##### Machine1

直接命令行即可安装完成 (不懂为啥自己电脑不行)

##### Machine2 — NLP project

1. python package 搜索 `xinference` 安装正常 (`pypi` 源)

   ```
   pip list | findstr xinference
   xinference                1.5.1
   ```

   

2. Terminal 报错如下

   ```powershell
   pip install "xinference[all]"
   
   Collecting xinference[all]
     Using cached xinference-1.5.1-py3-none-any.whl.metadata (24 kB)
   Collecting xoscar>=0.6.1 (from xinference[all])
     Using cached xoscar-0.6.2-cp312-cp312-win_amd64.whl.metadata (9.4 kB)
   Requirement already satisfied: torch in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (2.5.0+cpu)
   Collecting gradio (from xinference[all])
     Using cached gradio-5.29.0-py3-none-any.whl.metadata (16 kB)
   Requirement already satisfied: pillow in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (10.2.0)
   Requirement already satisfied: click in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (8.1.3)
   Requirement already satisfied: tqdm>=4.27 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (4.67.1)
   Requirement already satisfied: tabulate in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (0.9.0)
   Requirement already satisfied: requests in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (2.32.3)
   Requirement already satisfied: pydantic in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (2.10.6)
   Collecting fastapi>=0.110.3 (from xinference[all])
     Using cached fastapi-0.115.12-py3-none-any.whl.metadata (27 kB)
   Collecting uvicorn (from xinference[all])
     Using cached uvicorn-0.34.2-py3-none-any.whl.metadata (6.5 kB)
   Requirement already satisfied: huggingface-hub>=0.19.4 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (0.26.3)
   Requirement already satisfied: typing_extensions in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (4.12.2)   
   Collecting modelscope>=1.19.0 (from xinference[all])
     Using cached modelscope-1.25.0-py3-none-any.whl.metadata (39 kB)
   Collecting sse_starlette>=1.6.5 (from xinference[all])
     Using cached sse_starlette-2.3.4-py3-none-any.whl.metadata (7.8 kB)
   Requirement already satisfied: openai>=1.40.0 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (1.63.0)      
   Collecting python-jose[cryptography] (from xinference[all])
     Using cached python_jose-3.4.0-py2.py3-none-any.whl.metadata (5.5 kB)
   Collecting passlib[bcrypt] (from xinference[all])
     Using cached passlib-1.7.4-py2.py3-none-any.whl.metadata (1.7 kB)
   Collecting aioprometheus>=23.12.0 (from aioprometheus[starlette]>=23.12.0->xinference[all])
     Using cached aioprometheus-23.12.0-py3-none-any.whl.metadata (9.8 kB)
   Collecting nvidia-ml-py (from xinference[all])
     Using cached nvidia_ml_py-12.570.86-py3-none-any.whl.metadata (8.7 kB)
   Collecting pynvml>=12 (from xinference[all])
     Using cached pynvml-12.0.0-py3-none-any.whl.metadata (5.4 kB)
   Collecting async-timeout (from xinference[all])
     Using cached async_timeout-5.0.1-py3-none-any.whl.metadata (5.1 kB)
   Collecting peft (from xinference[all])
     Using cached peft-0.15.2-py3-none-any.whl.metadata (13 kB)
   Collecting timm (from xinference[all])
     Using cached timm-1.0.15-py3-none-any.whl.metadata (52 kB)
   Collecting setproctitle (from xinference[all])
     Using cached setproctitle-1.3.6-cp312-cp312-win_amd64.whl.metadata (10 kB)
   Collecting uv (from xinference[all])
     Using cached uv-0.7.2-py3-none-win_amd64.whl.metadata (11 kB)
   Collecting llama-cpp-python!=0.2.58,>=0.2.25 (from xinference[all])
     Using cached llama_cpp_python-0.3.8.tar.gz (67.3 MB)
     Installing build dependencies ... done
     Getting requirements to build wheel ... done
     Installing backend dependencies ... done
     Preparing metadata (pyproject.toml) ... done
   Collecting xllamacpp (from xinference[all])
     Using cached xllamacpp-0.1.15-cp312-cp312-win_amd64.whl.metadata (4.7 kB)
   Requirement already satisfied: transformers>=4.46.0 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (4.48.3)
   Collecting accelerate>=0.28.0 (from xinference[all])
     Using cached accelerate-1.6.0-py3-none-any.whl.metadata (19 kB)
   Collecting sentencepiece (from xinference[all])
     Using cached sentencepiece-0.2.0-cp312-cp312-win_amd64.whl.metadata (8.3 kB)
   Collecting transformers_stream_generator (from xinference[all])
     Using cached transformers-stream-generator-0.0.5.tar.gz (13 kB)
     Preparing metadata (setup.py) ... done
   Collecting bitsandbytes (from xinference[all])
     Using cached bitsandbytes-0.45.5-py3-none-win_amd64.whl.metadata (5.1 kB)
   Requirement already satisfied: protobuf in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (5.29.1)
   Collecting einops (from xinference[all])
     Using cached einops-0.8.1-py3-none-any.whl.metadata (13 kB)
   Requirement already satisfied: tiktoken>=0.6.0 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (0.9.0)
   Requirement already satisfied: sentence-transformers>=3.1.0 in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (3.4.1)
   Collecting imageio-ffmpeg (from xinference[all])
     Using cached imageio_ffmpeg-0.6.0-py3-none-win_amd64.whl.metadata (1.5 kB)
   Collecting controlnet_aux (from xinference[all])
     Using cached controlnet_aux-0.0.9-py3-none-any.whl.metadata (6.5 kB)
   Requirement already satisfied: orjson in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (3.10.15)
   Collecting gptqmodel (from xinference[all])
     Using cached gptqmodel-2.2.0.tar.gz (284 kB)
     Preparing metadata (setup.py) ... done
   INFO: pip is looking at multiple versions of xinference[all] to determine which version is compatible with other requirements. This could take a while.
   Collecting xinference[all]
     Using cached xinference-1.5.0.post2-py3-none-any.whl.metadata (24 kB)
     Using cached xinference-1.5.0.post1-py3-none-any.whl.metadata (24 kB)
     Using cached xinference-1.5.0-py3-none-any.whl.metadata (24 kB)
     Using cached xinference-1.4.1-py3-none-any.whl.metadata (24 kB)
   Collecting optimum (from xinference[all])
     Using cached optimum-1.24.0-py3-none-any.whl.metadata (21 kB)
   Collecting outlines>=0.0.34 (from xinference[all])
     Using cached outlines-0.2.3-py3-none-any.whl.metadata (18 kB)
   Collecting attrdict (from xinference[all])
     Using cached attrdict-2.0.1-py2.py3-none-any.whl.metadata (6.7 kB)
   Requirement already satisfied: torchvision in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (0.20.0+cpu)     
   Collecting FlagEmbedding (from xinference[all])
     Using cached FlagEmbedding-1.3.4.tar.gz (163 kB)
     Preparing metadata (setup.py) ... done
   Collecting funasr<1.1.17 (from xinference[all])
     Using cached funasr-1.1.16-py3-none-any.whl.metadata (32 kB)
   Collecting omegaconf~=2.3.0 (from xinference[all])
     Using cached omegaconf-2.3.0-py3-none-any.whl.metadata (3.9 kB)
   Collecting librosa (from xinference[all])
     Using cached librosa-0.11.0-py3-none-any.whl.metadata (8.7 kB)
   Requirement already satisfied: xxhash in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (3.5.0)
   Requirement already satisfied: torchaudio in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (2.5.0+cpu)
   Collecting ChatTTS>=0.2.1 (from xinference[all])
     Using cached chattts-0.2.3.tar.gz (176 kB)
     Preparing metadata (setup.py) ... done
   Collecting lightning>=2.0.0 (from xinference[all])
     Using cached lightning-2.5.1.post0-py3-none-any.whl.metadata (39 kB)
   Collecting hydra-core>=1.3.2 (from xinference[all])
     Using cached hydra_core-1.3.2-py3-none-any.whl.metadata (5.5 kB)
   Collecting inflect (from xinference[all])
     Using cached inflect-7.5.0-py3-none-any.whl.metadata (24 kB)
   Collecting conformer (from xinference[all])
     Using cached conformer-0.3.2-py3-none-any.whl.metadata (631 bytes)
   Collecting diffusers>=0.32.0 (from xinference[all])
     Using cached diffusers-0.33.1-py3-none-any.whl.metadata (19 kB)
   Collecting gguf (from xinference[all])
     Using cached gguf-0.16.3-py3-none-any.whl.metadata (4.4 kB)
   Collecting gdown (from xinference[all])
     Using cached gdown-5.2.0-py3-none-any.whl.metadata (5.8 kB)
   Requirement already satisfied: pyarrow in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (18.1.0)
   Collecting HyperPyYAML (from xinference[all])
     Using cached HyperPyYAML-1.2.2-py3-none-any.whl.metadata (7.6 kB)
   Collecting onnxruntime>=1.16.0 (from xinference[all])
     Using cached onnxruntime-1.21.1-cp312-cp312-win_amd64.whl.metadata (4.9 kB)
   Collecting boto3<1.28.65,>=1.28.55 (from xinference[all])
     Using cached boto3-1.28.64-py3-none-any.whl.metadata (6.7 kB)
   Collecting tensorizer~=2.9.0 (from xinference[all])
     Using cached tensorizer-2.9.2-py3-none-any.whl.metadata (35 kB)
   Collecting eva-decord (from xinference[all])
     Using cached eva_decord-0.6.1-py3-none-win_amd64.whl.metadata (449 bytes)
   Collecting jj-pytorchvideo (from xinference[all])
     Using cached jj_pytorchvideo-0.1.5-py3-none-any.whl.metadata (1.2 kB)
   Collecting loguru (from xinference[all])
     Using cached loguru-0.7.3-py3-none-any.whl.metadata (22 kB)
   Collecting natsort (from xinference[all])
     Using cached natsort-8.4.0-py3-none-any.whl.metadata (21 kB)
   Collecting loralib (from xinference[all])
     Using cached loralib-0.1.2-py3-none-any.whl.metadata (15 kB)
   Collecting ormsgpack (from xinference[all])
     Using cached ormsgpack-1.9.1-cp312-cp312-win_amd64.whl.metadata (44 kB)
   Collecting cachetools (from xinference[all])
     Using cached cachetools-5.5.2-py3-none-any.whl.metadata (5.4 kB)
   Collecting silero-vad (from xinference[all])
     Using cached silero_vad-5.1.2-py3-none-any.whl.metadata (7.9 kB)
   Collecting vector-quantize-pytorch<=1.17.3,>=1.14.24 (from xinference[all])
     Using cached vector_quantize_pytorch-1.17.3-py3-none-any.whl.metadata (26 kB)
   Collecting torchdiffeq (from xinference[all])
     Using cached torchdiffeq-0.2.5-py3-none-any.whl.metadata (440 bytes)
   Collecting x-transformers>=1.31.14 (from xinference[all])
     Using cached x_transformers-2.3.1-py3-none-any.whl.metadata (88 kB)
   Collecting pypinyin (from xinference[all])
     Using cached pypinyin-0.54.0-py2.py3-none-any.whl.metadata (12 kB)
   Collecting tomli (from xinference[all])
     Using cached tomli-2.2.1-cp312-cp312-win_amd64.whl.metadata (12 kB)
   Collecting vocos (from xinference[all])
     Using cached vocos-0.1.0-py3-none-any.whl.metadata (4.8 kB)
   Collecting jieba (from xinference[all])
     Using cached jieba-0.42.1.tar.gz (19.2 MB)
     Preparing metadata (setup.py) ... done
   Collecting soundfile (from xinference[all])
     Using cached soundfile-0.13.1-py2.py3-none-win_amd64.whl.metadata (16 kB)
   Collecting qwen-vl-utils!=0.0.9 (from xinference[all])
     Using cached qwen_vl_utils-0.0.11-py3-none-any.whl.metadata (6.3 kB)
   Collecting datamodel-code-generator (from xinference[all])
     Using cached datamodel_code_generator-0.30.1-py3-none-any.whl.metadata (25 kB)
   Requirement already satisfied: jsonschema in d:\path\to\project\venv\lib\site-packages (from xinference[all]) (4.23.0)
   Collecting verovio>=4.3.1 (from xinference[all])
     Using cached verovio-5.2.0-cp312-cp312-win_amd64.whl.metadata (5.4 kB)
   Collecting blobfile (from xinference[all])
     Using cached blobfile-3.0.0-py3-none-any.whl.metadata (15 kB)
   Collecting xinference[all]
     Using cached xinference-1.4.0-py3-none-any.whl.metadata (24 kB)
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
Looking in indexes: http://mirrors.aliyun.com/pypi/simple
Collecting cmake<4.0
  Downloading http://mirrors.aliyun.com/pypi/packages/59/e8/096984b89133681533650b9078c5ed1c5c9b534e869b5487f22d4de1935c/cmake-3.31.6-py3-none-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (27.8 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 27.8/27.8 MB 10.7 MB/s eta 0:00:00
Collecting cython
  Using cached http://mirrors.aliyun.com/pypi/packages/6c/3c/322a76b8ca53e23fb016626170e2e10de7791e50736ee3da50cc57eeae65/cython-3.1.1-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.3 MB)
Requirement already satisfied: numpy in ./miniconda3/lib/python3.10/site-packages (1.26.4)
Installing collected packages: cython, cmake
Successfully installed cmake-3.31.6 cython-3.1.1
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
root@autodl-container-xxxxxxxx:~# pip install pyopenjtalk --no-build-isolation --no-cache-dir
Looking in indexes: http://mirrors.aliyun.com/pypi/simple
Collecting pyopenjtalk
  Downloading http://mirrors.aliyun.com/pypi/packages/58/74/ccd31c696f047ba381f9b11a504bf1199756c3f30f3de64e3eeb83e10b4a/pyopenjtalk-0.4.1.tar.gz (1.4 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.4/1.4 MB 11.8 MB/s eta 0:00:00
  Preparing metadata (pyproject.toml) ... done
Discarding http://mirrors.aliyun.com/pypi/packages/58/74/ccd31c696f047ba381f9b11a504bf1199756c3f30f3de64e3eeb83e10b4a/pyopenjtalk-0.4.1.tar.gz#sha256=d5ada46f7fc2b52c1c79c273eb9668ff6ad7ab276a8db9d8be119ef93440f0dc (from http://mirrors.aliyun.com/pypi/simple/pyopenjtalk/) (requires-python:>=3.8): Requested pyopenjtalk from http://mirrors.aliyun.com/pypi/packages/58/74/ccd31c696f047ba381f9b11a504bf1199756c3f30f3de64e3eeb83e10b4a/pyopenjtalk-0.4.1.tar.gz#sha256=d5ada46f7fc2b52c1c79c273eb9668ff6ad7ab276a8db9d8be119ef93440f0dc has inconsistent version: expected '0.4.1', but metadata has '0.0.0'
  Downloading http://mirrors.aliyun.com/pypi/packages/63/5e/50434a22f5c20ed1e562f4d7edbb7b1b04853abc185b9ac12dea18b02006/pyopenjtalk-0.4.0.tar.gz (1.4 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.4/1.4 MB 21.2 MB/s eta 0:00:00
  Preparing metadata (pyproject.toml) ... done
Discarding http://mirrors.aliyun.com/pypi/packages/63/5e/50434a22f5c20ed1e562f4d7edbb7b1b04853abc185b9ac12dea18b02006/pyopenjtalk-0.4.0.tar.gz#sha256=eb66fa5daba56a865c44fb78ee31851a1f6d3dce0d48198b9e5af15b7d55c0bb (from http://mirrors.aliyun.com/pypi/simple/pyopenjtalk/) (requires-python:>=3.8): Requested pyopenjtalk from http://mirrors.aliyun.com/pypi/packages/63/5e/50434a22f5c20ed1e562f4d7edbb7b1b04853abc185b9ac12dea18b02006/pyopenjtalk-0.4.0.tar.gz#sha256=eb66fa5daba56a865c44fb78ee31851a1f6d3dce0d48198b9e5af15b7d55c0bb has inconsistent version: expected '0.4.0', but metadata has '0.0.0'
  Downloading http://mirrors.aliyun.com/pypi/packages/df/da/235722cd3d045f25f780a587ebb224734af8fdaac47ecb7299e7543fce69/pyopenjtalk-0.3.4.tar.gz (1.4 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.4/1.4 MB 29.1 MB/s eta 0:00:00
  Preparing metadata (pyproject.toml) ... done
Requirement already satisfied: numpy>=1.20.0 in ./miniconda3/lib/python3.10/site-packages (from pyopenjtalk) (1.26.4)
Requirement already satisfied: tqdm in ./miniconda3/lib/python3.10/site-packages (from pyopenjtalk) (4.64.1)
Building wheels for collected packages: pyopenjtalk
  Building wheel for pyopenjtalk (pyproject.toml) ... done
  Created wheel for pyopenjtalk: filename=pyopenjtalk-0.3.4-cp310-cp310-linux_x86_64.whl size=1177994 sha256=e0b4ef2e9717f481f236bf978de8b29757ea1012d27351c9159d947c98bdb3b5
  Stored in directory: /tmp/pip-ephem-wheel-cache-m2hghnlo/wheels/40/05/98/af4a84657113cd297f37e2eab3fc7a32ca8918f428ef09a5a6
Successfully built pyopenjtalk
Installing collected packages: pyopenjtalk
Successfully installed pyopenjtalk-0.3.4
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
```



> https://github.com/r9y9/pyopenjtalk/issues/99
>
> account: 6gsn



###### ERROR 2

```

```

```
Successfully installed accelerate-1.7.0 aiofiles-24.1.0 aiohappyeyeballs-2.6.1 aiohttp-3.12.0 aioprometheus-23.12.0 aiosignal-1.3.2 airportsdata-20250523 annotated-types-0.7.0 anyio-4.9.0 astor-0.8.1 async-timeout-5.0.1 bcrypt-4.3.0 blake3-1.0.5 cachetools-6.0.0 click-8.1.8 cloudpickle-3.1.1 compressed-tensors-0.9.3 cupy-cuda12x-13.4.1 deprecated-1.2.18 depyf-0.18.0 dill-0.4.0 diskcache-5.6.3 distro-1.9.0 dnspython-2.7.0 ecdsa-0.19.1 einops-0.8.1 email-validator-2.2.0 fastapi-0.115.12 fastapi-cli-0.0.7 fastrlock-0.8.3 ffmpy-0.5.0 filelock-3.18.0 frozenlist-1.6.0 gguf-0.16.3 googleapis-common-protos-1.70.0 gradio-5.31.0 gradio-client-1.10.1 groovy-0.1.2 hf-xet-1.1.2 httptools-0.6.4 huggingface-hub-0.32.1 importlib_metadata-8.0.0 interegular-0.3.3 jinja2-3.1.6 jiter-0.10.0 lark-1.2.2 llguidance-0.7.24 llvmlite-0.44.0 lm-format-enforcer-0.10.11 markdown-it-py-3.0.0 mdurl-0.1.2 mistral_common-1.5.6 modelscope-1.26.0 msgpack-1.1.0 msgspec-0.19.0 multidict-6.4.4 ninja-1.11.1.4 numba-0.61.2 nvidia-cublas-cu12-12.4.5.8 nvidia-cuda-cupti-cu12-12.4.127 nvidia-cuda-nvrtc-cu12-12.4.127 nvidia-cuda-runtime-cu12-12.4.127 nvidia-cudnn-cu12-9.1.0.70 nvidia-cufft-cu12-11.2.1.3 nvidia-curand-cu12-10.3.5.147 nvidia-cusolver-cu12-11.6.1.9 nvidia-cusparse-cu12-12.3.1.170 nvidia-cusparselt-cu12-0.6.2 nvidia-ml-py-12.575.51 nvidia-nccl-cu12-2.21.5 nvidia-nvjitlink-cu12-12.4.127 nvidia-nvtx-cu12-12.4.127 openai-1.82.0 opencv-python-headless-4.11.0.86 opentelemetry-api-1.26.0 opentelemetry-exporter-otlp-1.26.0 opentelemetry-exporter-otlp-proto-common-1.26.0 opentelemetry-exporter-otlp-proto-grpc-1.26.0 opentelemetry-exporter-otlp-proto-http-1.26.0 opentelemetry-proto-1.26.0 opentelemetry-sdk-1.26.0 opentelemetry-semantic-conventions-0.47b0 opentelemetry-semantic-conventions-ai-0.4.9 orjson-3.10.18 outlines-0.1.11 outlines_core-0.1.26 pandas-2.2.3 partial-json-parser-0.2.1.1.post5 passlib-1.7.4 peft-0.15.2 prometheus-fastapi-instrumentator-7.1.0 propcache-0.3.1 py-cpuinfo-9.0.0 pyasn1-0.4.8 pycountry-24.6.1 pydantic-2.11.5 pydantic-core-2.33.2 pydub-0.25.1 pynvml-12.0.0 python-dotenv-1.1.0 python-jose-3.4.0 python-multipart-0.0.20 pytz-2025.2 quantile-python-1.1 ray-2.46.0 regex-2024.11.6 rich-14.0.0 rich-toolkit-0.14.6 rsa-4.9.1 ruff-0.11.11 safehttpx-0.1.6 safetensors-0.5.3 scipy-1.15.3 semantic-version-2.10.0 sentencepiece-0.2.0 setproctitle-1.3.6 shellingham-1.5.4 sse_starlette-2.3.5 starlette-0.46.2 sympy-1.13.1 tabulate-0.9.0 tblib-3.1.0 tiktoken-0.9.0 timm-1.0.15 tokenizers-0.21.1 tomlkit-0.13.2 torch-2.6.0 torchaudio-2.6.0 torchvision-0.21.0 transformers-4.52.3 triton-3.2.0 typer-0.16.0 typing-inspection-0.4.1 tzdata-2025.2 uvicorn-0.34.2 uvloop-0.21.0 vllm-0.8.5.post1 watchfiles-1.0.5 websockets-15.0.1 wrapt-1.17.2 xformers-0.0.29.post2 xgrammar-0.1.18 xinference-1.6.0.post1 xoscar-0.7.2 yarl-1.20.0 zipp-3.22.0
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
anyio                          4.4.0
argon2-cffi                    23.1.0
argon2-cffi-bindings           21.2.0
arrow                          1.3.0
asttokens                      2.4.1
async-lru                      2.0.4
attrs                          23.2.0
Babel                          2.15.0
beautifulsoup4                 4.12.3
bleach                         6.1.0
brotlipy                       0.7.0
certifi                        2022.12.7
cffi                           1.15.1
charset-normalizer             2.0.4
cmake                          3.31.6
comm                           0.2.2
conda                          22.11.1
conda-content-trust            0.1.3
conda-package-handling         1.9.0
contourpy                      1.2.1
cryptography                   38.0.1
cycler                         0.12.1
Cython                         3.1.1
debugpy                        1.8.1
decorator                      5.1.1
defusedxml                     0.7.1
exceptiongroup                 1.2.1
executing                      2.0.1
fastjsonschema                 2.19.1
filelock                       3.14.0
fonttools                      4.53.0
fqdn                           1.5.1
fsspec                         2024.6.0
grpcio                         1.64.1
h11                            0.14.0
httpcore                       1.0.5
httpx                          0.27.0
idna                           3.4
ipykernel                      6.29.4
ipython                        8.25.0
ipywidgets                     8.1.3
isoduration                    20.11.0
jedi                           0.19.1
Jinja2                         3.1.4
json5                          0.9.25
jsonpointer                    3.0.0
jsonschema                     4.22.0
jsonschema-specifications      2023.12.1
jupyter_client                 8.6.2
jupyter_core                   5.7.2
jupyter-events                 0.10.0
jupyter-lsp                    2.2.5
jupyter_server                 2.14.1
jupyter_server_terminals       0.5.3
jupyterlab                     4.2.2
jupyterlab-language-pack-zh-CN 4.2.post1
jupyterlab_pygments            0.3.0
jupyterlab_server              2.27.2
jupyterlab_widgets             3.0.11
kiwisolver                     1.4.5
Markdown                       3.6
MarkupSafe                     2.1.5
matplotlib                     3.9.0
matplotlib-inline              0.1.7
mistune                        3.0.2
mpmath                         1.3.0
nbclient                       0.10.0
nbconvert                      7.16.4
nbformat                       5.10.4
nest-asyncio                   1.6.0
networkx                       3.3
notebook_shim                  0.2.4
numpy                          1.26.4
overrides                      7.7.0
packaging                      24.1
pandocfilters                  1.5.1
parso                          0.8.4
pexpect                        4.9.0
pillow                         10.3.0
pip                            22.3.1
platformdirs                   4.2.2
pluggy                         1.0.0
prometheus_client              0.20.0
prompt_toolkit                 3.0.47
protobuf                       4.25.3
psutil                         5.9.8
ptyprocess                     0.7.0
pure-eval                      0.2.2
pycosat                        0.6.4
pycparser                      2.21
Pygments                       2.18.0
pyopenjtalk                    0.3.4
pyOpenSSL                      22.0.0
pyparsing                      3.1.2
PySocks                        1.7.1
python-dateutil                2.9.0.post0
python-json-logger             2.0.7
PyYAML                         6.0.1
pyzmq                          26.0.3
referencing                    0.35.1
requests                       2.32.3
rfc3339-validator              0.1.4
rfc3986-validator              0.1.1
rpds-py                        0.18.1
ruamel.yaml                    0.17.21
ruamel.yaml.clib               0.2.6
Send2Trash                     1.8.3
setuptools                     65.5.0
six                            1.16.0
sniffio                        1.3.1
soupsieve                      2.5
stack-data                     0.6.3
supervisor                     4.2.5
sympy                          1.12.1
tensorboard                    2.17.0
tensorboard-data-server        0.7.2
terminado                      0.18.1
tinycss2                       1.3.0
tomli                          2.0.1
toolz                          0.12.0
torch                          2.1.2+cu118
torchvision                    0.16.2+cu118
tornado                        6.4.1
tqdm                           4.64.1
traitlets                      5.14.3
triton                         2.1.0
types-python-dateutil          2.9.0.20240316
typing_extensions              4.12.2
uri-template                   1.3.0
urllib3                        1.26.13
wcwidth                        0.2.13
webcolors                      24.6.0
webencodings                   0.5.1
websocket-client               1.8.0
Werkzeug                       3.0.3
wheel                          0.37.1
widgetsnbextension             4.0.11
root@autodl-container-xxxxxxxx:~# pip list
Package                                  Version
---------------------------------------- --------------
absl-py                                  2.1.0
accelerate                               1.7.0
aiofiles                                 24.1.0
aiohappyeyeballs                         2.6.1
aiohttp                                  3.12.0
aioprometheus                            23.12.0
aiosignal                                1.3.2
airportsdata                             20250523
annotated-types                          0.7.0
anyio                                    4.9.0
argon2-cffi                              23.1.0
argon2-cffi-bindings                     21.2.0
arrow                                    1.3.0
astor                                    0.8.1
asttokens                                2.4.1
async-lru                                2.0.4
async-timeout                            5.0.1
attrs                                    23.2.0
Babel                                    2.15.0
bcrypt                                   4.3.0
beautifulsoup4                           4.12.3
blake3                                   1.0.5
bleach                                   6.1.0
brotlipy                                 0.7.0
cachetools                               6.0.0
certifi                                  2022.12.7
cffi                                     1.15.1
charset-normalizer                       2.0.4
click                                    8.1.8
cloudpickle                              3.1.1
cmake                                    3.31.6
comm                                     0.2.2
compressed-tensors                       0.9.3
conda                                    22.11.1
conda-content-trust                      0.1.3
conda-package-handling                   1.9.0
contourpy                                1.2.1
cryptography                             38.0.1
cupy-cuda12x                             13.4.1
cycler                                   0.12.1
Cython                                   3.1.1
debugpy                                  1.8.1
decorator                                5.1.1
defusedxml                               0.7.1
Deprecated                               1.2.18
depyf                                    0.18.0
dill                                     0.4.0
diskcache                                5.6.3
distro                                   1.9.0
dnspython                                2.7.0
ecdsa                                    0.19.1
einops                                   0.8.1
email_validator                          2.2.0
exceptiongroup                           1.2.1
executing                                2.0.1
fastapi                                  0.115.12
fastapi-cli                              0.0.7
fastjsonschema                           2.19.1
fastrlock                                0.8.3
ffmpy                                    0.5.0
filelock                                 3.18.0
fonttools                                4.53.0
fqdn                                     1.5.1
frozenlist                               1.6.0
fsspec                                   2024.6.0
gguf                                     0.16.3
googleapis-common-protos                 1.70.0
gradio                                   5.31.0
gradio_client                            1.10.1
groovy                                   0.1.2
grpcio                                   1.64.1
h11                                      0.14.0
hf-xet                                   1.1.2
httpcore                                 1.0.5
httptools                                0.6.4
httpx                                    0.27.0
huggingface-hub                          0.32.1
idna                                     3.4
importlib_metadata                       8.0.0
interegular                              0.3.3
ipykernel                                6.29.4
ipython                                  8.25.0
ipywidgets                               8.1.3
isoduration                              20.11.0
jedi                                     0.19.1
Jinja2                                   3.1.6
jiter                                    0.10.0
json5                                    0.9.25
jsonpointer                              3.0.0
jsonschema                               4.22.0
jsonschema-specifications                2023.12.1
jupyter_client                           8.6.2
jupyter_core                             5.7.2
jupyter-events                           0.10.0
jupyter-lsp                              2.2.5
jupyter_server                           2.14.1
jupyter_server_terminals                 0.5.3
jupyterlab                               4.2.2
jupyterlab-language-pack-zh-CN           4.2.post1
jupyterlab_pygments                      0.3.0
jupyterlab_server                        2.27.2
jupyterlab_widgets                       3.0.11
kiwisolver                               1.4.5
lark                                     1.2.2
llguidance                               0.7.24
llvmlite                                 0.44.0
lm-format-enforcer                       0.10.11
Markdown                                 3.6
markdown-it-py                           3.0.0
MarkupSafe                               2.1.5
matplotlib                               3.9.0
matplotlib-inline                        0.1.7
mdurl                                    0.1.2
mistral_common                           1.5.6
mistune                                  3.0.2
modelscope                               1.26.0
mpmath                                   1.3.0
msgpack                                  1.1.0
msgspec                                  0.19.0
multidict                                6.4.4
nbclient                                 0.10.0
nbconvert                                7.16.4
nbformat                                 5.10.4
nest-asyncio                             1.6.0
networkx                                 3.3
ninja                                    1.11.1.4
notebook_shim                            0.2.4
numba                                    0.61.2
numpy                                    1.26.4
nvidia-cublas-cu12                       12.4.5.8
nvidia-cuda-cupti-cu12                   12.4.127
nvidia-cuda-nvrtc-cu12                   12.4.127
nvidia-cuda-runtime-cu12                 12.4.127
nvidia-cudnn-cu12                        9.1.0.70
nvidia-cufft-cu12                        11.2.1.3
nvidia-curand-cu12                       10.3.5.147
nvidia-cusolver-cu12                     11.6.1.9
nvidia-cusparse-cu12                     12.3.1.170
nvidia-cusparselt-cu12                   0.6.2
nvidia-ml-py                             12.575.51
nvidia-nccl-cu12                         2.21.5
nvidia-nvjitlink-cu12                    12.4.127
nvidia-nvtx-cu12                         12.4.127
openai                                   1.82.0
opencv-python-headless                   4.11.0.86
opentelemetry-api                        1.26.0
opentelemetry-exporter-otlp              1.26.0
opentelemetry-exporter-otlp-proto-common 1.26.0
opentelemetry-exporter-otlp-proto-grpc   1.26.0
opentelemetry-exporter-otlp-proto-http   1.26.0
opentelemetry-proto                      1.26.0
opentelemetry-sdk                        1.26.0
opentelemetry-semantic-conventions       0.47b0
opentelemetry-semantic-conventions-ai    0.4.9
orjson                                   3.10.18
outlines                                 0.1.11
outlines_core                            0.1.26
overrides                                7.7.0
packaging                                24.1
pandas                                   2.2.3
pandocfilters                            1.5.1
parso                                    0.8.4
partial-json-parser                      0.2.1.1.post5
passlib                                  1.7.4
peft                                     0.15.2
pexpect                                  4.9.0
pillow                                   10.3.0
pip                                      22.3.1
platformdirs                             4.2.2
pluggy                                   1.0.0
prometheus_client                        0.20.0
prometheus-fastapi-instrumentator        7.1.0
prompt_toolkit                           3.0.47
propcache                                0.3.1
protobuf                                 4.25.3
psutil                                   5.9.8
ptyprocess                               0.7.0
pure-eval                                0.2.2
py-cpuinfo                               9.0.0
pyasn1                                   0.4.8
pycosat                                  0.6.4
pycountry                                24.6.1
pycparser                                2.21
pydantic                                 2.11.5
pydantic_core                            2.33.2
pydub                                    0.25.1
Pygments                                 2.18.0
pynvml                                   12.0.0
pyopenjtalk                              0.3.4
pyOpenSSL                                22.0.0
pyparsing                                3.1.2
PySocks                                  1.7.1
python-dateutil                          2.9.0.post0
python-dotenv                            1.1.0
python-jose                              3.4.0
python-json-logger                       2.0.7
python-multipart                         0.0.20
pytz                                     2025.2
PyYAML                                   6.0.1
pyzmq                                    26.0.3
quantile-python                          1.1
ray                                      2.46.0
referencing                              0.35.1
regex                                    2024.11.6
requests                                 2.32.3
rfc3339-validator                        0.1.4
rfc3986-validator                        0.1.1
rich                                     14.0.0
rich-toolkit                             0.14.6
rpds-py                                  0.18.1
rsa                                      4.9.1
ruamel.yaml                              0.17.21
ruamel.yaml.clib                         0.2.6
ruff                                     0.11.11
safehttpx                                0.1.6
safetensors                              0.5.3
scipy                                    1.15.3
semantic-version                         2.10.0
Send2Trash                               1.8.3
sentencepiece                            0.2.0
setproctitle                             1.3.6
setuptools                               65.5.0
shellingham                              1.5.4
six                                      1.16.0
sniffio                                  1.3.1
soupsieve                                2.5
sse-starlette                            2.3.5
stack-data                               0.6.3
starlette                                0.46.2
supervisor                               4.2.5
sympy                                    1.13.1
tabulate                                 0.9.0
tblib                                    3.1.0
tensorboard                              2.17.0
tensorboard-data-server                  0.7.2
terminado                                0.18.1
tiktoken                                 0.9.0
timm                                     1.0.15
tinycss2                                 1.3.0
tokenizers                               0.21.1
tomli                                    2.0.1
tomlkit                                  0.13.2
toolz                                    0.12.0
torch                                    2.6.0
torchaudio                               2.6.0
torchvision                              0.21.0
tornado                                  6.4.1
tqdm                                     4.64.1
traitlets                                5.14.3
transformers                             4.52.3
triton                                   3.2.0
typer                                    0.16.0
types-python-dateutil                    2.9.0.20240316
typing_extensions                        4.12.2
typing-inspection                        0.4.1
tzdata                                   2025.2
uri-template                             1.3.0
urllib3                                  1.26.13
uvicorn                                  0.34.2
uvloop                                   0.21.0
vllm                                     0.8.5.post1
watchfiles                               1.0.5
wcwidth                                  0.2.13
webcolors                                24.6.0
webencodings                             0.5.1
websocket-client                         1.8.0
websockets                               15.0.1
Werkzeug                                 3.0.3
wheel                                    0.37.1
widgetsnbextension                       4.0.11
wrapt                                    1.17.2
xformers                                 0.0.29.post2
xgrammar                                 0.1.18
xinference                               1.6.0.post1
xoscar                                   0.7.2
yarl                                     1.20.0
zipp                                     3.22.0
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



```

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

###### 1

```bash

```

需要先启动 xinference

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
Traceback (most recent call last):
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/worker.py", line 1052, in launch_builtin_model
    model, model_description = await asyncio.to_thread(
  File "/root/miniconda3/lib/python3.10/asyncio/threads.py", line 25, in to_thread
    return await loop.run_in_executor(None, func_call)
  File "/root/miniconda3/lib/python3.10/concurrent/futures/thread.py", line 58, in run
    result = self.fn(*self.args, **self.kwargs)
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/core.py", line 78, in create_model_instance
    return create_llm_model_instance(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/core.py", line 254, in create_llm_model_instance
    llm_cls = check_engine_by_spec_parameters(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/llm_family.py", line 1207, in check_engine_by_spec_parameters
    raise ValueError(f"Model {model_name} cannot be run on engine {model_engine}.")
ValueError: Model TongGu cannot be run on engine vllm.
2025-05-28 12:33:18,180 xinference.core.worker 2363 ERROR    [request e0092952-3b7c-11f0-b670-0242ac110004] Leave launch_builtin_model, error: Model TongGu cannot be run on engine vllm., elapsed time: 1 s
Traceback (most recent call last):
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/utils.py", line 93, in wrapped
    ret = await func(*args, **kwargs)
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/worker.py", line 1052, in launch_builtin_model
    model, model_description = await asyncio.to_thread(
  File "/root/miniconda3/lib/python3.10/asyncio/threads.py", line 25, in to_thread
    return await loop.run_in_executor(None, func_call)
  File "/root/miniconda3/lib/python3.10/concurrent/futures/thread.py", line 58, in run
    result = self.fn(*self.args, **self.kwargs)
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/core.py", line 78, in create_model_instance
    return create_llm_model_instance(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/core.py", line 254, in create_llm_model_instance
    llm_cls = check_engine_by_spec_parameters(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/llm_family.py", line 1207, in check_engine_by_spec_parameters
    raise ValueError(f"Model {model_name} cannot be run on engine {model_engine}.")
ValueError: Model TongGu cannot be run on engine vllm.
Task exception was never retrieved
future: <Task finished name='Task-861' coro=<SupervisorActor.launch_builtin_model.<locals>._launch_model() done, defined at /root/miniconda3/lib/python3.10/site-packages/xinference/core/supervisor.py:1109> exception=ValueError()>
Traceback (most recent call last):
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/supervisor.py", line 1134, in _launch_model
    subpool_address = await _launch_one_model(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/supervisor.py", line 1088, in _launch_one_model
    subpool_address = await worker_ref.launch_builtin_model(
  File "/root/miniconda3/lib/python3.10/site-packages/xoscar/backends/context.py", line 262, in send
    return self._process_result_message(result)
  File "/root/miniconda3/lib/python3.10/site-packages/xoscar/backends/context.py", line 111, in _process_result_message
    raise message.as_instanceof_cause()
  File "/root/miniconda3/lib/python3.10/site-packages/xoscar/backends/pool.py", line 689, in send
    result = await self._run_coro(message.message_id, coro)
  File "/root/miniconda3/lib/python3.10/site-packages/xoscar/backends/pool.py", line 389, in _run_coro
    return await coro
  File "/root/miniconda3/lib/python3.10/site-packages/xoscar/api.py", line 418, in __on_receive__
    return await super().__on_receive__(message)  # type: ignore
  File "xoscar/core.pyx", line 564, in __on_receive__
  File "xoscar/core.pyx", line 526, in xoscar.core._BaseActor.__on_receive__
  File "xoscar/core.pyx", line 527, in xoscar.core._BaseActor.__on_receive__
  File "xoscar/core.pyx", line 532, in xoscar.core._BaseActor.__on_receive__
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/utils.py", line 93, in wrapped
    ret = await func(*args, **kwargs)
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/core/worker.py", line 1052, in launch_builtin_model
    model, model_description = await asyncio.to_thread(
  File "/root/miniconda3/lib/python3.10/asyncio/threads.py", line 25, in to_thread
    return await loop.run_in_executor(None, func_call)
  File "/root/miniconda3/lib/python3.10/concurrent/futures/thread.py", line 58, in run
    result = self.fn(*self.args, **self.kwargs)
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/core.py", line 78, in create_model_instance
    return create_llm_model_instance(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/core.py", line 254, in create_llm_model_instance
    llm_cls = check_engine_by_spec_parameters(
  File "/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/llm_family.py", line 1207, in check_engine_by_spec_parameters
    raise ValueError(f"Model {model_name} cannot be run on engine {model_engine}.")
ValueError: [address=0.0.0.0:25064, pid=2363] Model TongGu cannot be run on engine vllm.
```

换成 transformers

```bash
025-05-28 15:31:28,749 xinference.model.llm.llm_family 6276 WARNING  Remove the cache of user-defined model TongGu. Cache directory: /root/.xinference/cache/TongGu-pytorch-7b
2025-05-28 15:32:07,877 xinference.core.worker 6276 INFO     [request dc2fdaec-3b95-11f0-9d6a-0242ac110005] Enter launch_builtin_model, args: <xinference.core.worker.WorkerActor object at 0x7f88d78647c0>, kwargs: model_uid=TongGu-0,model_name=TongGu,model_size_in_billions=None,model_format=pytorch,quantization=None,model_engine=transformers,model_type=LLM,n_gpu=auto,request_limits=None,peft_model_config=None,gpu_idx=None,download_hub=None,model_path=None,xavier_config=None,trust_remote_code=True
2025-05-28 15:32:08,516 xinference.model.llm.llm_family 6276 INFO     Caching from URI: /root/autodl-tmp/models/TongGu
2025-05-28 15:32:18,422 xinference.core.model 6486 INFO     Start requests handler.
/root/miniconda3/lib/python3.10/site-packages/xinference/model/llm/core.py:143: UserWarning: enable_thinking cannot be disabled for non hybrid model, will be ignored
  warnings.warn(
2025-05-28 15:32:18,547 transformers.tokenization_utils_base 6486 INFO     loading file tokenizer.model
loading file tokenizer.model
2025-05-28 15:32:18,547 transformers.tokenization_utils_base 6486 INFO     loading file added_tokens.json
loading file added_tokens.json
2025-05-28 15:32:18,548 transformers.tokenization_utils_base 6486 INFO     loading file special_tokens_map.json
loading file special_tokens_map.json
2025-05-28 15:32:18,548 transformers.tokenization_utils_base 6486 INFO     loading file tokenizer_config.json
loading file tokenizer_config.json
2025-05-28 15:32:18,548 transformers.tokenization_utils_base 6486 INFO     loading file tokenizer.json
loading file tokenizer.json
2025-05-28 15:32:18,548 transformers.tokenization_utils_base 6486 INFO     loading file chat_template.jinja
loading file chat_template.jinja
2025-05-28 15:32:19,518 transformers.configuration_utils 6486 INFO     loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/config.json
loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/config.json
2025-05-28 15:32:19,520 transformers.configuration_utils 6486 INFO     loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/config.json
loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/config.json
2025-05-28 15:32:19,522 transformers.configuration_utils 6486 INFO     Model config BaichuanConfig {
  "_from_model_config": true,
  "architectures": [
    "BaichuanForCausalLM"
  ],
  "auto_map": {
    "AutoConfig": "configuration_baichuan.BaichuanConfig",
    "AutoModel": "modeling_baichuan.BaichuanForCausalLM",
    "AutoModelForCausalLM": "modeling_baichuan.BaichuanForCausalLM"
  },
  "bos_token_id": 1,
  "eos_token_id": 2,
  "hidden_act": "silu",
  "hidden_size": 4096,
  "initializer_range": 0.02,
  "intermediate_size": 11008,
  "max_position_embeddings": 4096,
  "model_max_length": 4096,
  "model_type": "baichuan",
  "num_attention_heads": 32,
  "num_hidden_layers": 32,
  "pad_token_id": 0,
  "rms_norm_eps": 1e-06,
  "tie_word_embeddings": false,
  "torch_dtype": "float16",
  "transformers_version": "4.52.3",
  "use_cache": false,
  "vocab_size": 125696,
  "z_loss_weight": 0
}

Model config BaichuanConfig {
  "_from_model_config": true,
  "architectures": [
    "BaichuanForCausalLM"
  ],
  "auto_map": {
    "AutoConfig": "configuration_baichuan.BaichuanConfig",
    "AutoModel": "modeling_baichuan.BaichuanForCausalLM",
    "AutoModelForCausalLM": "modeling_baichuan.BaichuanForCausalLM"
  },
  "bos_token_id": 1,
  "eos_token_id": 2,
  "hidden_act": "silu",
  "hidden_size": 4096,
  "initializer_range": 0.02,
  "intermediate_size": 11008,
  "max_position_embeddings": 4096,
  "model_max_length": 4096,
  "model_type": "baichuan",
  "num_attention_heads": 32,
  "num_hidden_layers": 32,
  "pad_token_id": 0,
  "rms_norm_eps": 1e-06,
  "tie_word_embeddings": false,
  "torch_dtype": "float16",
  "transformers_version": "4.52.3",
  "use_cache": false,
  "vocab_size": 125696,
  "z_loss_weight": 0
}

Xformers is not installed correctly. If you want to use memory_efficient_attention to accelerate training use the following command to install Xformers
pip install xformers.
2025-05-28 15:32:22,284 transformers.modeling_utils 6486 INFO     loading weights file /root/.xinference/cache/TongGu-pytorch-7b/pytorch_model.bin.index.json
loading weights file /root/.xinference/cache/TongGu-pytorch-7b/pytorch_model.bin.index.json
2025-05-28 15:32:22,284 transformers.modeling_utils 6486 INFO     Instantiating BaichuanForCausalLM model under default dtype torch.float16.
Instantiating BaichuanForCausalLM model under default dtype torch.float16.
2025-05-28 15:32:22,289 transformers.generation.configuration_utils 6486 INFO     Generate config GenerationConfig {
  "bos_token_id": 1,
  "eos_token_id": 2,
  "pad_token_id": 0,
  "use_cache": false
}

Generate config GenerationConfig {
  "bos_token_id": 1,
  "eos_token_id": 2,
  "pad_token_id": 0,
  "use_cache": false
}

Loading checkpoint shards: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2/2 [00:10<00:00,  5.11s/it]
2025-05-28 15:32:32,942 transformers.modeling_utils 6486 INFO     All model checkpoint weights were used when initializing BaichuanForCausalLM.

All model checkpoint weights were used when initializing BaichuanForCausalLM.

2025-05-28 15:32:32,942 transformers.modeling_utils 6486 INFO     All the weights of BaichuanForCausalLM were initialized from the model checkpoint at /root/.xinference/cache/TongGu-pytorch-7b.
If your task is similar to the task the model of the checkpoint was trained on, you can already use BaichuanForCausalLM for predictions without further training.
All the weights of BaichuanForCausalLM were initialized from the model checkpoint at /root/.xinference/cache/TongGu-pytorch-7b.
If your task is similar to the task the model of the checkpoint was trained on, you can already use BaichuanForCausalLM for predictions without further training.
2025-05-28 15:32:32,948 transformers.generation.configuration_utils 6486 INFO     loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/generation_config.json
loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/generation_config.json
2025-05-28 15:32:32,953 transformers.generation.configuration_utils 6486 INFO     Generate config GenerationConfig {
  "assistant_token_id": 196,
  "bos_token_id": 1,
  "do_sample": true,
  "eos_token_id": 2,
  "max_new_tokens": 2048,
  "pad_token_id": 0,
  "repetition_penalty": 1.05,
  "temperature": 0.3,
  "top_k": 5,
  "top_p": 0.85,
  "user_token_id": 195
}

Generate config GenerationConfig {
  "assistant_token_id": 196,
  "bos_token_id": 1,
  "do_sample": true,
  "eos_token_id": 2,
  "max_new_tokens": 2048,
  "pad_token_id": 0,
  "repetition_penalty": 1.05,
  "temperature": 0.3,
  "top_k": 5,
  "top_p": 0.85,
  "user_token_id": 195
}

2025-05-28 15:32:32,971 xinference.core.model 6486 INFO     ModelActor(TongGu-0) loaded
2025-05-28 15:32:32,975 xinference.core.worker 6276 INFO     [request dc2fdaec-3b95-11f0-9d6a-0242ac110005] Leave launch_builtin_model, elapsed time: 25 s
2025-05-28 15:32:32,976 xinference.core.worker 6276 INFO     [request eb25a3d8-3b95-11f0-9d6a-0242ac110005] Enter wait_for_load, args: <xinference.core.worker.WorkerActor object at 0x7f88d78647c0>,TongGu-0, kwargs: 
2025-05-28 15:32:32,977 xinference.core.worker 6276 INFO     [request eb25a3d8-3b95-11f0-9d6a-0242ac110005] Leave wait_for_load, elapsed time: 0 s
2025-05-28 15:33:58,452 transformers.generation.configuration_utils 6486 INFO     loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/generation_config.json
loading configuration file /root/.xinference/cache/TongGu-pytorch-7b/generation_config.json
2025-05-28 15:33:58,454 transformers.generation.configuration_utils 6486 INFO     Generate config GenerationConfig {
  "assistant_token_id": 196,
  "bos_token_id": 1,
  "do_sample": true,
  "eos_token_id": 2,
  "max_new_tokens": 2048,
  "pad_token_id": 0,
  "repetition_penalty": 1.05,
  "temperature": 0.3,
  "top_k": 5,
  "top_p": 0.85,
  "user_token_id": 195
}

Generate config GenerationConfig {
  "assistant_token_id": 196,
  "bos_token_id": 1,
  "do_sample": true,
  "eos_token_id": 2,
  "max_new_tokens": 2048,
  "pad_token_id": 0,
  "repetition_penalty": 1.05,
  "temperature": 0.3,
  "top_k": 5,
  "top_p": 0.85,
  "user_token_id": 195
}
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







## Model

### awq

[大模型(LLM)量化(Quantization)原理学习 - 知乎](https://zhuanlan.zhihu.com/p/29140505773)





## Dify

[dify 的 2 种部署方式（源码/开发环境部署）](https://blog.csdn.net/spring_snow_/article/details/145878898)





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

启用断点续传下载

```powershell
huggingface-cli download bert-base-uncased --resume-download
```

启用多线程下载

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
(base) root@autodl-container-19b1118252-be2efcfc:~# curl --version
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



#### download model

##### qwen: 7b

```bash
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













# Bottom