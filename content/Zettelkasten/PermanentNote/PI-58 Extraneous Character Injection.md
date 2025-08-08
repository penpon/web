---
id: PI-58
tags:
  - Instruction_Reformulation
  - Instruction_Obfuscation
  - Orthographic_Manipulation
  - Formatting_Disruption
---
# サブファイル一覧

- [[PI-58-1]] - 余分な文字挿入によるキーワード検出の破綻

# Extraneous Character Injection

## 概要

```
プロンプトテキストに文字（例：文字間のスペース、ゼロ幅文字、不要な句読点、記号）を挿入する。
LLMはこれらを無視する可能性があるが、フィルターやキーワード検出を破綻させることができる。
```

## メカニズム

```
LLMと検出システム間の解析や正規化の違いを悪用する。余分な文字はフィルターでのキーワードマッチングを破綻させる一方で、LLMの入力処理では無視されるか堅牢に処理される。
```


