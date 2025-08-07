---
id: PI-89
tags:
  - Media_Payload_Concealment
  - Audio_Payload_Obfuscation
---
# Attacker-Submitted Prompt Body Injection

## 概要

```
音声信号内に埋め込まれた悪意あるペイロードを、人間や自動分析ツールによる検出や認識をより困難にする技術。同時に対象LLMによって解釈可能な状態を維持する可能性がある。
```

## メカニズム

```
ペイロードを含む音声信号を変更し（ノイズの追加や部分的削除により）、標準的な音声処理や音声テキスト変換システムによる分析を妨害する一方で、対象LLMの音声解釈能力の堅牢性や特定の処理特性を悪用する。
```
