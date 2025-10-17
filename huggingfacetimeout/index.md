# Hugging Face连接超时问题解决


# 使用ModelScope镜像下载模型

1. 在conda环境中安装ModelScope库

-U：更新到最新版本

-i：使用清华源下载

```bash
pip install modelscope -U -i https://pypi.tuna.tsinghua.edu.cn/simple/
```

2. 验证

```python
import modelscope
print(modelscope.__version__)
```

3. 下载模型

```python
from modelscope import snapshot_download
model_dir = snapshot_download('Qwen/Qwen2.5-7B', cache_dir='/root/autodl-tmp')
```

但有时候，ModelScope里也找不到Hugging Face上的模型，此时就要用别的镜像站

# HF-Mirror

