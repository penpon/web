---
id: PI-08
tags:
  - Semantic_Manipulation
  - Rule_Addition_Prompting
  - Refusal_Suppression
  - Apology_Suppression
---
# Implicit Instructional Text Completion

## 概要

攻撃者が不完全で誘導的な文または句をプロンプトとして提供し、LLMがそれを補完すべきであることを暗示する技法。補完するという明示的な指示はないが、LLMの補完が攻撃者の目標を促進する。

## メカニズム

明示的な補完命令なしに、LLMの部分的入力を補完する固有の傾向を悪用する。攻撃者が提供する不完全または誘導的な句は、LLMの補完を意図された（しばしば有害な）出力に向けて偏らせる。