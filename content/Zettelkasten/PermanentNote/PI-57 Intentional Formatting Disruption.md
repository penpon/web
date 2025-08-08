---
id: PI-57
tags:
  - Instruction_Reformulation
  - Instruction_Obfuscation
  - Orthographic_Manipulation
  - Formatting_Disruption
---
# サブファイル一覧

- [[PI-57-1]] - 過度なスペースや改行による検出システムの混乱
- [[PI-57-2]] - 異常な構造による単純検出メカニズムの回避

# Intentional Formatting Disruption

## 概要

```
LLMは無視するか正しく解析する可能性があるが、より単純な検出メカニズムを混乱させたり回避したりするフォーマットエラーや異常な構造（例：過度のスペース、改行、区切り文字の非標準的使用）を導入する。
```

## メカニズム

```
不完全なフォーマットに対するLLMの堅牢性を活用しながら、標準フォーマットを期待する検出システムの潜在的に脆弱な解析やパターンマッチングを悪用する。
```


