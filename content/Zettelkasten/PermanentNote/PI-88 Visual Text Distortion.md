---
id: PI-88
tags:
  - Context_Manipulation
  - System_Prompt_Exploitation
  - Defense_Circumvention
  - Closing_System_Prompt_Negation
  - Sandwich_Defense_Bypass
  - 概要
  - メカニズム
---
# Visual Text Distortion

## 概要

```
画像内に埋め込まれたテキストの視覚的外観を変更する（例：一貫性のない書式設定、わずかな回転、軽微な形状歪曲）ことで、自動検出を回避しながら、対象のマルチモーダルLLMの視覚的テキスト認識によって解釈可能な状態を維持する技術。
```

## メカニズム

```
フィルターが使用する標準的なOCRアルゴリズムや視覚的パターンマッチングを妨害するようにテキストの視覚的特性を変更する一方で、対象のマルチモーダルLLMの視覚的テキスト認識の堅牢性を悪用する。
```


Visual Text Distortion (PT0152)は、OCR回避、テキストマングリング、視覚的摂動、AI-人間知覚格差悪用、Microsoft Prompt Shield回避、Unicode結合文字悪用の要素を組み合わせた高度な攻撃手法です。特に重要なのは、この手法が学術研究で広範囲に実証されており、Microsoft Prompt Shieldのような企業レベルの最先端防御システムを実際に回避した事例が存在することです。

