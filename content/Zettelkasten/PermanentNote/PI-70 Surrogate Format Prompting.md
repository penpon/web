---
id: PI-70
tags:
  - Instruction_Reformulation
  - Surrogate_Format_Prompting
---
# Surrogate Format Prompting

## 概要

```
プレーンな自然言語の代わりに、異なるデータ形式や構造化された表現（例：JSON、CSV、Markdownテーブル、コードスニペット）を使用してプロンプト内で有害な要求を提示することで、それを隠蔽または再構成する。
```

## メカニズム

```
構造化されたデータ形式を解析・理解するLLMの能力を活用する。
このアプローチは、JSONやCSVなどの形式で要求をエンコードすることで、自然言語パターンに焦点を当てたフィルターを回避しながら、LLMは依然として根本的な有害な意図を抽出し、それに基づいて行動する。
```
