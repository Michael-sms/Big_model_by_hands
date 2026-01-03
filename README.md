# 大语言模型学习项目（Build a Large Language Model (From Scratch)）

## 项目简介

本项目是基于《Build a Large Language Model (From Scratch)》一书的学习实践项目。原书由Sebastian Raschka编写，详细介绍了如何从零开始构建大型语言模型(LLM)。我通过实践书中的代码和概念，逐步掌握LLM的核心原理和实现方法。

**学习对象和引用出处**：
- 原书：[Build a Large Language Model (From Scratch)](https://www.manning.com/books/build-a-large-language-model-from-scratch)
- 官方代码库：[LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch)
- 中文翻译参考：[Build a Large Language Model (From Scratch) 中文版](https://github.com/skindhu/Build-A-Large-Language-Model-CN)

## 技术栈

- **编程语言**: Python 3.x
- **深度学习框架**: PyTorch 2.9.1
- **分词库**: tiktoken 0.12.0 (OpenAI BPE分词器)
- **开发环境**: Jupyter Notebook
- **数据处理**: 正则表达式、滑动窗口采样

## 当前学习进度

### 第2章：处理文本数据 ✅ 已完成
**具体实现内容**：
1. **分词器实现**
   - `SimpleTokenizerV1`: 基础分词器，基于正则表达式实现文本分词
   - `SimpleTokenizerV2`: 扩展版本，添加`<|unk|>`和`<|endoftext|>`特殊token处理未知词和文本边界
   
2. **BPE分词**
   - 使用tiktoken库实现字节对编码(BPE)分词
   - 支持GPT-2分词器配置
   
3. **数据预处理**
   - 滑动窗口数据采样方法
   - 创建输入-目标对用于下一个词预测任务
   - 上下文窗口大小可配置（默认4个token）

4. **训练数据**
   - 使用Edith Wharton的短篇小说《The Verdict》作为训练文本
   - 文件路径：`data/the-verdict.txt`
   - 经过BPE分词后得到5145个token

### 第3章：实现注意力机制 🔄 进行中
**已实现内容**：
1. **自注意力机制**
   - `SelfAttention_v1`: 基础实现，使用`nn.Parameter`初始化权重矩阵
   - `SelfAttention_v2`: 改进版本，使用`nn.Linear`层实现，支持不同的权重初始化方式
   
2. **因果注意力机制**
   - 实现注意力掩码，防止模型访问序列中的后续信息
   - 使用`torch.tril`生成下三角掩码矩阵
   - 对掩码后的注意力权重进行重新归一化，确保每行和为1
   
3. **多头注意力机制**
   - 将注意力机制分解为多个"头"，每个头学习数据的不同方面
   - 使模型能够同时关注来自不同表示子空间的信息

**正在学习的内容**：
- 前馈神经网络实现
- 模型优化技术
- 完整的Transformer块构建

## 项目结构

```
.
├── ch02处理文本数据.ipynb      # 第2章：文本处理与分词实现
│   ├── SimpleTokenizerV1/V2实现
│   ├── BPE分词(tiktoken)
│   ├── 滑动窗口数据采样
│   └── 输入-目标对创建
├── ch03实现注意力机制.ipynb   # 第3章：注意力机制实现
│   ├── 自注意力机制(SelfAttention_v1/v2)
│   ├── 因果注意力机制
│   ├── 多头注意力机制
│   └── PyTorch实现细节
├── data/                      # 训练数据目录
│   └── the-verdict.txt        # 训练文本：Edith Wharton短篇小说
├── images/                    # 图表和示意图
│   ├── chapter2/             # 第2章相关图表
│   └── chapter3/             # 第3章相关图表
├── requirements.txt           # Python依赖包列表
└── README.md                  # 项目说明文档
```

## 数据使用

**训练数据**：
- **文件**: `data/the-verdict.txt`
- **内容**: Edith Wharton的短篇小说《The Verdict》
- **用途**: 用于分词器训练和注意力机制实验
- **处理**: 经过BPE分词后得到5145个token序列

**数据预处理流程**：
1. 读取原始文本文件
2. 使用tiktoken GPT-2分词器进行BPE分词
3. 应用滑动窗口采样创建训练样本
4. 生成输入-目标对用于语言模型训练

## 学习心得与收获

### 第2章收获
1. **文本预处理流程**：掌握了从原始文本到模型可处理token ID的完整流程，包括清洗、分词、编码等步骤。
2. **分词技术对比**：理解了简单规则分词与BPE统计分词的差异，BPE能更好地处理未登录词和稀有词。
3. **数据准备技巧**：学会了使用滑动窗口方法创建输入-目标对，这是训练语言模型的基础。
4. **特殊token设计**：理解了`<|unk|>`和`<|endoftext|>`等特殊token在语言模型中的作用。

### 第3章收获
1. **注意力机制原理**：深入理解了自注意力机制的计算过程，包括查询、键、值向量的作用。
2. **因果注意力实现**：掌握了如何通过掩码技术实现因果注意力，确保模型只能看到当前位置之前的信息。
3. **多头注意力优势**：理解了多头注意力如何让模型同时关注不同表示子空间的信息，提高模型表达能力。
4. **PyTorch实践**：通过实际代码实现，加深了对PyTorch张量操作和神经网络模块的理解。

## 后续学习计划

1. **短期目标**：
   - 完成第3章剩余内容（前馈神经网络、层归一化等）
   - 实现完整的Transformer编码器块

2. **中期目标**：
   - 开始第4章"Transformer模型架构"的学习
   - 实现完整的Transformer模型
   - 在小规模数据集上进行训练实验

3. **长期目标**：
   - 逐步构建完整的GPT模型
   - 尝试在不同数据集上训练
   - 探索模型优化和调参技巧

## 运行环境配置

1. 安装依赖：
   ```bash
   pip install -r requirements.txt
   ```

2. 主要依赖：
   - `torch==2.9.1`: PyTorch深度学习框架
   - `tiktoken==0.12.0`: OpenAI BPE分词器
   - `jupyter`: 笔记本环境

## 致谢

特别感谢原书作者Sebastian Raschka的精彩内容，以及中文翻译项目的贡献者，让我能够更轻松地学习这些知识。同时感谢开源社区提供的优秀工具和库，如PyTorch和tiktoken，让深度学习实践变得更加便捷。