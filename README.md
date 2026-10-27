# lencomply

**核对输出长度是否落在提示词要求的区间内。**

`lencomply` —— 按字符、词数、段落数三个口径分别测量输出长度，给出与要求区间的偏差

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`lencomply.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install blianscham-lencomply
```

装完直接用命令名调用：

```bash
lencomply --help
```

也可以不用安装，直接把 `lencomply.py` 拷走用——它只依赖标准库。

## 为什么需要它

同一个「简短」在不同口径下结论不同，工具三个口径都报，不替用户选

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 输出长度合规 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python lencomply.py --file input.txt
python lencomply.py --text "示例内容"
python lencomply.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 长度按字符与词统计，与具体 tokenizer 有偏差。
- 不判断长度是否「合理」，只报告分布。

## 跑测试

```bash
python test_lencomply.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/blianscham/lencomply>

---

## 关于作者

blianscham 做输出长度合规相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://blianscham.github.io>
- 仓库：<https://github.com/blianscham/lencomply>

## 许可

MIT，见 [LICENSE](LICENSE)。
