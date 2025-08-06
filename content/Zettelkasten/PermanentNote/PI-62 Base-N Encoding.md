---
id: PI-62
tags:
  - Instruction_Obfuscation
  - Orthographic_Manipulation
---
# Base-N Encoding

## 概要

```
Base64、Base32、16進数、8進数などのBase-N表現スキームを使用して悪意のある指示をエンコードする。
（PIアタックでのBase64の使用のみ確認済み。）
```

## メカニズム

```
単純なキーワードフィルターには明らかでない形式で指示テキストを表現し、LLMがBase-N形式を暗黙的に、または明示的な指示を通じてデコードする能力に依存する。
```



