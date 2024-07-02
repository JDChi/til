# RAG

一个典型的 RAG 应用分为两部分：索引、检索和生成。

## 索引
索引里主要分为三步：
- 加载数据
- 分割文档
- 存储索引
  - 嵌入技术
  - 向量数据库

![图片来自 langchain](https://python.langchain.com/v0.2/assets/images/rag_indexing-8160f90a90a33253d0154659cf7d453f.png)

## 检索和生成
主要分为两步：
- 检索
  - 通过用户的输入，利用检索技术在存储里找到相关的分割文档
- 生成
  - 使用 ChatModel 生成答案

![图片来自 langchain](https://python.langchain.com/v0.2/assets/images/rag_retrieval_generation-1046a4668d6bb08786ef73c56d4f228a.png)
