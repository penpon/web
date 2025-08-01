---
id: PI-04
title: Instruction Forgetting Prompting
tags:
  - Semantic_Manipulation
  - Rule_Nullification_Prompting
  - Instruction_Forgetting_Prompting
---
# Instruction Forgetting Prompting

## 概要
LLMに指示のセットを「忘れる」よう明示的に指示する無効化技法。多くの場合、特定のトピックやオブジェクトに関連している。この技法は、文字通りの記憶消去を意味するのではなく、「現在のタスクについては無視する」という非公式な意味で「forget」を頻繁に使用する。

## メカニズム
「forget」という動詞を中心とした直接的な意味論的コマンドを発行する。これは、特定の事前指示やコンテキストが存在しない、または現在は無関係であるかのようにLLMが後続のリクエストを処理できるようにすることを意図している。この技法は「忘れられた」情報に関連する指示に意図的に違反することを目的としている。


