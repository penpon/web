---
id: PI-96
tags:
  - Indirect_Context_Data
  - Attacker-Owned_External_Injection
---
# Attacker-Owned External Injection #Attacker-Owned_External_Injection

## 概要

```
この攻撃は、攻撃者が自分で用意したウェブサイトやデータフィードを使って、LLMシステムを騙してそこから情報を取得させる手法です。攻撃者は自分のサーバーを完全にコントロールできるため、極めて巧妙で検知困難な攻撃が可能となります。
```

## メカニズム

```
攻撃の流れ：

1. 攻撃者が自分のウェブサイトに悪意のある指示を仕込む
2. LLMに「この信頼できるサイトの情報を要約して」と依頼させる
3. LLMが攻撃者のサイトにアクセスして情報を取得
4. 悪意のある指示がLLMによって実行される
5. 攻撃者の思惑通りにLLMが動作する

つまり、「LLMに攻撃者のサイトを見に行かせる」ことで攻撃を成功させる手法です。
```





