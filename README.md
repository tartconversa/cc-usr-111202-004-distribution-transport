# 传感器分布漂移的运输解释与界证书

本项目保存虚构科学工程分析的合成输入与Python读取工具。当前工具仅解析输入并显示类型和条数，不执行参数拟合、统计分析、方程求解、优化或模型训练。所有仪器、实验、研究与专家身份均为虚构。

## 数据口径

点位置只用于解释位移，cost与allowed边显式给出。probability为质量，禁止边不在edges里；source和target各自质量和为1，不能自动重标。

fixtures保存原始输入，src/transport_reader.py是当前读取器，material-index.json为文件内容摘要。研究计算输出可写到独立.workspace-output目录，输入不应被覆盖。

## 本地运行

Python 3.11及以上；已有读取工具仅依赖标准库，无第三方安装步骤。进入项目根目录执行：

    python -m src.transport_reader fixtures/transport.json

编译检查：

    python -m compileall -q src tests

输入契约验证：

    python -m unittest discover -s tests -v

## 固定容器

    docker build -t distribution-transport:local .
    docker run --rm distribution-transport:local

容器按完整镜像摘要固定，默认运行读取测试，不访问外部实验系统。
