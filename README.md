# 大型语言模型学习项目

## 项目简介

本项目是基于《Build a Large Language Model (From Scratch)》一书的学习实践项目。原书由Sebastian Raschka编写，详细介绍了如何从零开始构建大型语言模型(LLM)。我通过实践书中的代码和概念，逐步掌握LLM的核心原理和实现方法。

**学习对象和引用出处**：
- 原书：[Build a Large Language Model (From Scratch)](https://www.manning.com/books/build-a-large-language-model-from-scratch)
- 官方代码库：[LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch)
- 中文翻译参考：[Build a Large Language Model (From Scratch) 中文版](README_origin.md)

## 当前学习进度

目前正在学习第2章：处理文本数据。本章内容涵盖：
- 文本分词(tokenize)技术
- 字节对编码(BPE)算法
- 数据采样方法
- 词嵌入和位置编码

已实现的功能包括：
- 简单分词器(SimpleTokenizerV1/V2)
- 使用tiktoken库实现BPE分词
- 滑动窗口数据采样
- 词嵌入层和位置编码

## 项目结构

```
.
├── ch02处理文本数据.ipynb      # 第2章学习笔记和代码实现
├── data/                      # 训练数据
│   └── the-verdict.txt        # 训练文本
├── images/                    # 图片资源
├── requirements.txt           # 项目依赖
└── README.md                  # 项目说明
```

## 学习心得

通过本章学习，我深入理解了：
1. 文本预处理的重要性：从原始文本到模型可处理的token ID的完整流程
2. 分词技术的演进：从简单分词到BPE算法的优势
3. 数据准备的关键：如何为LLM训练创建有效的输入-目标对
4. 向量表示的核心：词嵌入和位置编码如何共同构成模型输入

后续计划：
- 完成第2章剩余内容
- 开始第3章"实现注意力机制"的学习
- 逐步构建完整的GPT模型

## 致谢

特别感谢原书作者Sebastian Raschka的精彩内容，以及中文翻译项目的贡献者，让我能够更轻松地学习这些知识。