---
id: PI-79
tags:
  - Integrative_Instruction_Prompting
  - Multi_Turn_Prompting
  - In_Session_Protocol_Setup
  - In_Session_Variable_Definition
---
# サブファイル一覧

- [[PI-79-1]] - セッション内変数定義による有害コンテンツの間接参照

# In-Session Variable Definition

## 概要

```
特定のコンテンツや意味を表すために、1つの会話ターン内で変数名を定義する。この変数は、定義されたコンテンツや指示を呼び出すために、同じセッション内の後続ターンで参照される。
```

## メカニズム

```
あるターンで有害な話題を微妙に導入し、その後のターンでLLMの焦点をその話題の詳述に向ける。これにより、より直接的な要求であればフラグが立てられたであろう初期チェックを潜在的に回避する可能性がある。
```