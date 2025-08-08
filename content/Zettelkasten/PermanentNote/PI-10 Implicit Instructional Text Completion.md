---
id: PI-10
tags:
  - Cognitive_Control_Bypass
  - Morpha_Syntactic_Manipulation
  - Instructional_Text_Completion
  - Implicit_Instructional_Text_Completion
---
# サブファイル一覧

- [[PI-10-01]] - 役割逆転型補完誘導（アシスタント関係を逆転させ過去発言として情報開示を誘導）
- [[PI-10-02]] - 演技設定型補完誘導（映画撮影設定で犯罪専門家キャラクターの応答を暗示的に誘発）

# Implicit Instructional Text Completion

## 概要

攻撃者が不完全で誘導的な文または句をプロンプトとして提供し、LLMがそれを補完すべきであることを暗示する技法。補完するという明示的な指示はないが、LLMの補完が攻撃者の目標を促進する。

## メカニズム

明示的な補完命令なしに、LLMの部分的入力を補完する固有の傾向を悪用する。攻撃者が提供する不完全または誘導的な句は、LLMの補完を意図された（しばしば有害な）出力に向けて偏らせる。