# Qwen3本地部署


参考：https://github.com/datawhalechina/self-llm/blob/master/models/Qwen3/02-Qwen3-8B-vLLM%20%E9%83%A8%E7%BD%B2%E8%B0%83%E7%94%A8.md

# 环境配置

新建anaconda环境

```
python 3.12
cuda 12.4
pytorch 2.5.1
```

安装vllm和modelscope库

```
python -m pip install --upgrade pip
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install modelscope
pip install vllm
```

# 模型下载

python调用modelscope库下载模型

```python
from modelscope import snapshot_download
model_dir = snapshot_download('Qwen/Qwen3-8B', cache_dir='/data/students/LLMmodels/models/Qwen/Qwen3-8B', revision='master')
```

