---
layout: default
title: Python FAQ
parent: Program Language
nav_order: 1
---

# Python FAQ

## 切换国内源

[清华源pypi](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)


#### 临时使用

```python
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```

注意，`simple` 不能少, 是 `https` 而不是 `http`

#### 设为默认

升级 pip 到最新的版本 (>=10.0.0) 后进行配置：

```
python -m pip install --upgrade pip
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

如果您到 pip 默认源的网络连接较差，临时使用本镜像站来升级 pip：

```bash
python -m pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade pip
```

#### 配置多个镜像源

如果您想配置多个镜像源平衡负载，可在已经替换 `index-url`的情况下通过以下方式继续增加源站：

```
pip config set global.extra-index-url "<url1> <url2>..."
```

请自行替换引号内的内容，源地址之间需要有空格

可用的 `pypi` 源列表（校园网联合镜像站）：[https://mirrors.cernet.edu.cn/list/pypi](https://mirrors.cernet.edu.cn/list/pypi)


# six

```python
pip install six --upgrade --ignore-installed six
``` 
