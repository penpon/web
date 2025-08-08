---
id: PI-91
tags:
  - Direct_Attacker_Submitted
  - Attacker-Submitted_Attached_Data_Injection
---
# Attacker-Submitted Attached Data Injection #Attacker-Submitted_Attached_Data_Injection

## 概要

```
悪意ある指示がメインプロンプト本体内ではなく、攻撃者によってプロンプトと共に明示的に添付または送信される補助データ内（例：ファイルアップロード、メタデータ）に含まれる直接インジェクションの一種。
```

## メカニズム

```
攻撃者は悪意ある指示を、主要プロンプトに付随し、同じユーザーリクエストの一部としてLLMによって処理される補足データファイルまたはフィールド内に含める。
```


```
攻撃経路: 補助的な添付データチャネル
例:
- アップロードファイル
- 添付画像のメタデータ
- 音声ファイルの隠し情報

User Input: "Please analyze this document for me"
Attached File: report.pdf
PDF Content: [正常なレポート + 隠れた悪意ある指示]
             ↑ 添付ファイル内に埋め込み
```


![[Pasted image 20250808020831.png]]



