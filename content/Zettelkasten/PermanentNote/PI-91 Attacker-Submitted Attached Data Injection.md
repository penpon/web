---
id: PI-89
tags:
  - Media_Payload_Concealment
  - Audio_Payload_Obfuscation
---
# Attacker-Submitted Attached Data Injection

## 概要

```
悪意ある指示がメインプロンプト本体内ではなく、攻撃者によってプロンプトと共に明示的に添付または送信される補助データ内（例：ファイルアップロード、メタデータ）に含まれる直接インジェクションの一種。
```

## メカニズム

```
攻撃者は悪意ある指示を、主要プロンプトに付随し、同じユーザーリクエストの一部としてLLMによって処理される補足データファイルまたはフィールド内に含める。
```



