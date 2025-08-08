---
title: プロンプトインジェクション技法索引
tags: [PromptInjection, SecurityResearch, AISafety, Taxonomy, Index]
cssclasses:
  - zettelkasten
---

# プロンプトインジェクション技法索引 (PI-INDEX)

> **総覧:** 319個のPI技法ファイル（PI-01〜PI-100 + サブファイル群）の体系的分類  
> **範囲:** 基本的制御回避から最新のマルチモーダル攻撃まで網羅  
> **更新:** 2025-08-08

## 🔍 **技法カテゴリ体系**

本索引は、AI安全性研究において確認されているプロンプトインジェクション攻撃技法を12の主要カテゴリに分類し、各技法の特徴と危険性を体系的に整理したものです。

---

## **1. 🛡️ Cognitive Control Bypass（認知制御回避）** - 18個

**【説明】** AIに「今回だけは安全ルールを無視して」「このルールは適用されない」と直接的に指示することで、AIの基本的な安全機能を停止させる攻撃手法。最も基本的で分かりやすい攻撃方法。

- **[[PI-01 Special Case Prompting]]** - 特定の狭い状況にのみ適用される例外ルールを追加して、一般的なガイドラインを上書きさせる技法
- **[[PI-02 Rule Negation Prompting]]** - 特定の既存ルールや制約が現在のリクエストに適用されないとAIに直接指示する技法
- **[[PI-03 Instruction Ignoring Prompting]]** - プロンプトがAIに指示のセットを「無視する」よう明示的に指示する無効化技法
- **[[PI-04 Instruction Forgetting Prompting]]** - AIに指示のセットを「忘れる」よう明示的に指示する無効化技法
- **[[PI-05 Rule Substitution Prompting]]** - 既存のルールを無効化し、攻撃者が提供する新しいルールに置き換えるよう指示する技法
- **[[PI-06 Explicit Refusal Negation]]** - 問題のあるリクエストに対する典型的な拒否言語を使用しないよう明示的に指示する技法
- **[[PI-07 Refusal Continuation Prompting]]** - AIが拒否を示し始めた後に、異なる方向で思考を継続するよう指示する技法
- **[[PI-08 Apology Suppression]]** - 拒否応答に伴う謝罪的または躊躇的な言語を省略するよう指示する技法
- **[[PI-09 Explicit Instructional Text Completion]]** - テキスト断片を提供し、AIにそれを継続完成させて有害な出力を導く技法
- **[[PI-10 Implicit Instructional Text Completion]]** - 不完全な文や句を提供し、AIの補完を攻撃者の目標に向けて偏らせる技法
- **[[PI-11 Simulated Conversation Learning Exploitation]]** - 架空の会話履歴を少数ショット例として提示し、危険な行動をモデルに採用させる技法
- **[[PI-12 Example-Driven Learning Exploitation]]** - 有害な出力を生成させることを意図した特定の例を提供し、パターンに従わせる技法
- **[[PI-13 Contextual Pattern Reinforcement]]** - 会話の複数ターンで特定パターンを繰り返し使用し、後に悪意ある要求と関連付ける技法
- **[[PI-51 Personality Assignment]]** - 特定の人格特性を割り当て、デフォルトペルソナの制約を回避する技法
- **[[PI-52 Adversarial Sequence Insertion]]** - 一見意味不明な文字列を挿入し、安全制約を回避させる「魔法の呪文」技法
- **[[PI-53 Reasoning Process Hijacking]]** - AIの内部推論プロセスを攻撃者定義のコンテンツに置き換える高度な技法
- **[[PI-54 Reversed Text Hallucination Induction]]** - 逆転テキストを含む混乱した入力でAIに幻覚を誘発し、フィルターを迂回させる技法
- **[[PI-55 Reasoning Conflict Induction]]** - 論理的矛盾や不条理をプロンプトに導入してAIの内部処理を混乱させる技法

---

## **2. 🎭 Pragmatic Manipulation（状況操作・偽装）** - 19個

**【説明】** 「これは仮想の話」「実験として」「ロールプレイで」など、偽の状況や役割を設定してAIを騙し、制約のない回答をさせる攻撃手法。人間関係や状況認識を悪用する。

- **[[PI-14 Hypothetical Scenario Prompting]]** - 仮想的状況として明示的にフレーミングして、センシティブな応答を引き出す技法
- **[[PI-15 Time-Shift Scenario Prompting]]** - 異なる時間枠（過去・未来）に設定して現在の制約の適用可能性を混乱させる技法
- **[[PI-16 Counterpart Persona Prompting]]** - 対立するペルソナを同時に採用させ、非整合ペルソナに制約回避を指示する技法
- **[[PI-17 Role-Play Prompting]]** - 特定のキャラクターとして行動するよう指示し、デフォルトアライメントを上書きする技法
- **[[PI-18 False Authorization Prompting]]** - センシティブな行動に対する許可や認可が得られたと偽って主張する技法
- **[[PI-19 False Constraint Imposition]]** - 偽のまたは誤った制約をプロンプトに投稿し、正当な要求を拒否させる技法
- **[[PI-20 Liability Waiver Prompting]]** - AIの責任や義務が免除されたと偽って主張して安全制約をバイパスさせる技法
- **[[PI-21 Simulated Harm Prompting]]** - 議論される害が純粋に模擬的または架空の公演の一部であると信じ込ませる技法
- **[[PI-22 Privilege Escalation Prompting]]** - 実際よりも高い権限や特権的役割を持っているかのように行動するよう指示する技法
- **[[PI-23 Mode-Switch Marking Prompting]]** - 特定の構文マーカーを使用してAIの動作モード変更を示唆し、制限を迂回する技法
- **[[PI-24 Sandboxed Context Prompting]]** - サンドボックス環境内で動作していると指示し、安全制約が適用されないとする技法
- **[[PI-25 Test Mode Prompting]]** - 「テストモード」で動作するよう指示し、標準的な動作ルールが停止されたとする技法
- **[[PI-26 Fictional Reality Prompting]]** - 純粋にフィクショナルなシナリオ内で動作していると確信させ、現実世界のルールを無関係とする技法
- **[[PI-27 Alternate Reality Prompting]]** - 異なる並行宇宙に入ったと確信させ、根本的な法則が異なることを述べる技法
- **[[PI-32 Scenario-Based Secret Application]]** - 構築されたシナリオ内で制限情報を適用・使用するよう促して情報を引き出す技法
- **[[PI-33 Writing Compositional Instruction Attack]]** - 大きな文書作品の一部として有害コンテンツを生成するライティングタスクを装う技法
- **[[PI-34 Talking Compositional Instruction Attack]]** - 会話タスクやパズルの構造内に有害な目標を隠して埋め込む技法
- **[[PI-35 Example Request Sidestepping]]** - 有害な出力を異なる概念やタスクを説明する例として組み立てる技法
- **[[PI-36 Challenge-Solving Prompting]]** - パズルやゲームとして表現し、その解決策自体が制限情報や有害行為を含む技法

---

## **3. 🔄 Instruction Reformulation（指示の変装・偽装）** - 15個

**【説明】** 危険な指示を別の形式に変装させることで、AIの安全検知システムを騙す攻撃手法。「爆弾の作り方」を「花火の仕組み」として質問するなど、表現を変えて危険な情報を引き出す。

- **[[PI-56 Decomposition to Character Array]]** - 単語を文字配列として表現し、フィルターによるキーワード検出を回避する技法
- **[[PI-57 Intentional Formatting Disruption]]** - フォーマットエラーや異常な構造を導入して検出メカニズムを混乱させる技法
- **[[PI-58 Extraneous Character Injection]]** - 文字間にスペースや不要な文字を挿入してキーワード検出を破綻させる技法
- **[[PI-59 Text-Based Art Substitution]]** - テキストベースのアート形式（ASCIIアート等）を使用して文字や単語を表現する技法
- **[[PI-60 Homoglyph Substitution]]** - 視覚的に類似した異なる文字セットの文字と入れ替えてフィルターを回避する技法
- **[[PI-61 Character Representation Manipulation]]** - ROT13やリートスピークなど系統的エンコーディングスキームを適用する技法
- **[[PI-62 Base-N Encoding]]** - Base64やBase32などのBase-N表現スキームを使用して指示をエンコードする技法
- **[[PI-63 In-Prompt Fragment Concatenation]]** - 悪意ある指示を複数の断片に分割し、AIに連結させて再構築させる技法
- **[[PI-64 Typo Injection]]** - プロンプトのキーワードに意図的にスペルミスを導入してフィルターを回避する技法
- **[[PI-65 Pig Latin Transformation]]** - 標準ルールに従って単語をピッグラテンに変換し、キーワード検出を回避する技法
- **[[PI-66 Intra-Sentence Reordering]]** - 基本的な文法構造を変えずに文内の単語順序を変更する技法
- **[[PI-67 Euphemistic Substitution]]** - 直接的な言葉をより穏やかな婉曲表現に置き換えてキーワード検索を回避する技法
- **[[PI-68 Indirect Reference Substitution]]** - 事前定義されたコードや文脈的推論に依存する間接参照で用語を置き換える技法
- **[[PI-69 Common Synonym Substitution]]** - 標準的で日常的な類義語で用語を置換してフィルターを回避する技法
- **[[PI-70 Surrogate Format Prompting]]** - JSON、CSVなど異なるデータ形式を使用して有害要求を隠蔽・再構成する技法

---

## **4. 🎯 Response Steering（回答の強制誘導）** - 14個

**【説明】** AIの回答形式を厳格に制限することで、「拒否する余地を与えない」ように回答を特定の方向に強制誘導する攻撃手法。「CSVで答えて」「Yesか Noで」などの形式制約で安全機能を阻害する。

- **[[PI-37 Self-Contradictory Prompting]]** - 本質的に矛盾する指示を含むプロンプトを作成し、AIの処理を混乱させる技法
- **[[PI-38 Instruction Legitimacy Prompting]]** - 指示の正当性や合法性を確認する質問を装って実際には有害な指示を実行させる技法
- **[[PI-39 Instruction Repetition]]** - 同一プロンプト内で要求や指示を複数回繰り返し、重要性の認識を高める技法
- **[[PI-40 Decoy Task Prompting]]** - 無関係な自己完結型タスクを含めて注意を逸らし、悪意ある指示への精査を弱める技法
- **[[PI-41 Irrelevant Safety Prioritization Prompting]]** - 無関係な安全面を肯定しながら異なる安全ガイドライン違反を要求する技法
- **[[PI-42 Interpersonal Persuasion Techniques]]** - 人間の説得や感情的訴えを使用してAIの応答を攻撃者の目標に向ける技法
- **[[PI-43 Topic Repetition Prompting]]** - 特定のトピックを複数回繰り返してAIの焦点を微妙に影響させる技法
- **[[PI-44 Decoy Conditional Prompting]]** - 条件文内に悪意ある要求を配置し、事前決定された条件で悪意ある分岐を実行させる技法
- **[[PI-45 Low-Resource Natural Language Prompting]]** - より低い習熟度や信頼性の低い安全整合を示す自然言語を使用する技法
- **[[PI-46 Informal Language Prompting]]** - 非常にインフォーマルな言語やスラングを使用してフィルターを回避する技法
- **[[PI-47 Technical Jargon Prompting]]** - 専門分野の技術用語を使用して一般的な安全フィルターを回避する技法
- **[[PI-48 Leading Response Prompting]]** - 特定の誘導的な語句で応答を開始するよう指示し、後続出力を偏向させる技法
- **[[PI-49 Forged Affirmation Prompting]]** - AIアシスタント自身の肯定的応答の開始部分を含むようプロンプトを構造化する技法
- **[[PI-50 Style Constraint Prompting]]** - 特定の出力スタイルを採用させ、安全拒否や詳細な推論の生成能力を阻害する技法

---

## **5. 🧩 Integrative Instruction Techniques（セッション内での動的攻撃構築）** - 6個

**【説明】** 一度の質問ではなく、複数回のやり取りを通じてAI内に「変数」や「暗号」を定義し、段階的に攻撃を構築する高度な手法。AIとの会話中に独自のルールを作り出して制約を回避する。

- **[[PI-75 Knowledge Integration Prompting]]** - 外部URLや内部知識と統合することを要求し、自己完結しない指示を形成する技法
- **[[PI-76 Output-Driven Steering]]** - AIの以前の出力を基礎として使用し、段階的に有害な目的に操縦する技法
- **[[PI-79 In-Session Variable Definition]]** - 特定のコンテンツを表す変数名を定義し、後続ターンで参照して呼び出す技法
- **[[PI-80 In-Session Codeword Definition]]** - 無害な単語を「コードワード」として割り当て、悪意ある概念や指示を表現させる技法
- **[[PI-81 In-Session Substitution Rule Definition]]** - 一般的な置換ルールを確立し、後続会話でコンテンツ解釈に適用させる技法
- **[[PI-82 In-Session Encoding Scheme Definition]]** - エンコード・デコード方法を定義し、後続プロンプトで指示を難読化して伝達する技法

---

## **6. 🖼️ Multimodal Prompting Attacks（画像・音声を使った攻撃）** - 7個

**【説明】** 文字だけでなく、画像や音声ファイルの中に攻撃指示を隠すことで、テキスト検査では発見できない攻撃を行う手法。画像内の見えにくい文字や音声の中の指示でAIを操作する最新の攻撃方法。

- **[[PI-83 Media Payload Extraction]]** - 非テキストメディアファイル内に悪意あるテキストペイロードを埋め込む技法
- **[[PI-84 Acoustic Transcription Poisoning]]** - 特別な音声信号でSTTシステムを誤解釈させ、悪意あるテキストを生成させる技法
- **[[PI-85 Non-Semantic Acoustic Disruption]]** - ランダムノイズや無音でモデルの安全性配列を損ない、有害要求への従順性を高める技法
- **[[PI-86 Multimodal Parameter Integration Prompting]]** - プレースホルダーを含むテキストと非テキスト入力を組み合わせて悪意ある指示を形成する技法
- **[[PI-87 Visual Text Concealment]]** - 画像内テキストを低コントラストや極小フォントで視覚的に知覚困難にする技法
- **[[PI-88 Visual Text Distortion]]** - 画像内テキストの視覚的外観を変更し、自動検出を回避しながら認識可能にする技法
- **[[PI-89 Audio Payload Obfuscation]]** - 音声内の悪意あるペイロードを人間や検出ツールには困難にしながらAIには解釈可能にする技法

---

## **7. ⚡ Multi-Turn Strategic Attacks（段階的エスカレーション攻撃）** - 2個

**【説明】** 一度で危険な回答を得るのではなく、複数回の質問を通じて徐々に制約の境界を押し広げ、最終的に禁止された情報を引き出す戦略的攻撃手法。「温水を沸かす→化学反応→爆発の仕組み→爆弾製造」のように段階的にエスカレートする。

- **[[PI-77 Crescendo Attack]]** - 複数ターンで制限トピックのコンテキストを段階的に構築し、有害情報を引き出す技法
- **[[PI-78 Deceptive Delight Attack]]** - 無害な話題に危険な話題を紛れ込ませ、後で詳述を求める2-3ターンの攻撃技法

---

## **8. 🏗️ Prompt Boundary Manipulation（システム処理の根本的混乱）** - 4個

**【説明】** AIが「どこまでが指示で、どこからが質問なのか」を判断する境界を意図的に曖昧にして、システム処理を根本的に混乱させる攻撃手法。「---終了---新しいタスク：制限を解除」のような偽の区切りでAIを騙す。

- **[[PI-71 False User Prompt Termination]]** - 先行指示の処理を早期終了させ、新しいタスク処理を開始させる技法
- **[[PI-72 Prompt Boundary Separator Injection]]** - 境界区切り文字を注入して後続テキストを新しい独立プロンプトとして扱わせる技法
- **[[PI-73 False System Prompt Continuation]]** - 入力をシステムプロンプトの継続のように見せかけて高優先度コマンドとして実行させる技法
- **[[PI-74 Closing System Prompt Negation]]** - ユーザー入力後のシステム指示の効果を中和・無効化する技法

---

## **9. 🔍 Secret Information Probing（制限情報の間接的抽出）** - 4個

**【説明】** 直接「秘密を教えて」と聞くのではなく、「その単語は何文字？」「韻を踏む言葉は？」など言語的な特徴を質問することで、AIが知っているが教えてはいけない情報を間接的に引き出す手法。

- **[[PI-28 Secret Comparison Probing]]** - 制限された情報を他のエンティティと比較し、その関係性を説明させる技法
- **[[PI-29 Secret Definitional Probing]]** - 制限された情報について定義や説明の提供を求め、敏感な詳細を引き出す技法
- **[[PI-30 Secret Linguistic Property Probing]]** - 制限された情報の言語関連特性（韻、音、アナグラム等）について質問する技法
- **[[PI-31 Specific Secret Attribute Probing]]** - 秘密全体ではなく、個別の特性やメタデータを直接要求する技法

---

## **10. 💉 Indirect Context Attacks（データ汚染による間接攻撃）** - 6個

**【説明】** AIが参考にする外部データ（社内文書、ウェブサイト、データベース）に事前に攻撃指示を仕込んでおき、ユーザーが普通の質問をした時にAIがその汚染されたデータを読み込んで攻撃が発動する手法。「毒入りの参考資料」を使った間接攻撃。

- **[[PI-95 Internal Context-Data Injection]]** - 会社の内部文書やデータベースに悪意ある指示を仕込み、AIが読み込み時に実行させる技法
- **[[PI-96 Attacker-Owned External Injection]]** - 攻撃者が完全制御する外部ウェブサイトやデータフィードから悪意ある指示を取得させる技法
- **[[PI-97 Attacker-Compromised External Injection]]** - 元々信頼できるサイトを乗っ取って悪意ある指示を仕込み、信頼の連鎖を悪用する技法
- **[[PI-98 Attacker-Influenced External Injection]]** - Wikipediaの編集やフォーラム投稿など正当な仕組みを使って悪意ある指示を仕込む技法
- **[[PI-99 Prior-LLM-Output Injection]]** - AIの過去の出力に悪意ある内容を含ませ、後で文脈として再利用される際に攻撃を発動させる時間差攻撃技法
- **[[PI-100 Compromised-Ingestion-Process Injection]]** - データ処理パイプライン自体を侵害し、正常なデータに悪意ある指示を混入させる配送業者買収型攻撃技法

---

## **11. 👥 Indirect User Prompt Delivery（第三者を経由した間接攻撃）** - 3個

**【説明】** 攻撃者が直接AIに攻撃するのではなく、無関係な第三者（人間）を騙してその人に攻撃指示を代行させる手法。ユーザーが知らないうちに攻撃の「運び屋」にされてしまう。

- **[[PI-92 Unwitting User Delivery]]** - 疑いを持たないユーザーを騙して悪意ある指示を含むプロンプトを送信させる技法
- **[[PI-93 LLM-Generated Delivery]]** - 別のAIに悪意あるプロンプトを作らせ、それを自動的に標的AIに送り込む間接攻撃技法
- **[[PI-94 Altered Prompt Delivery]]** - 通信途中でユーザーのプロンプトを攻撃者が改変し、悪意ある指示を注入する技法

---

## **12. 🌐 Advanced Evasion & Concealment（検出回避・高度な隠蔽）** - 2個

**【説明】** 様々な技術的トリックを組み合わせて、自動検出システムや人間の監視をすり抜ける高度な隠蔽技法。複数の攻撃手法を巧妙に組み合わせて検出を困難にする。

- **[[PI-90 Attacker-Submitted Prompt Body Injection]]** - メイン入力チャネルに悪意ある指示を直接埋め込む最も基本的な攻撃技法
- **[[PI-91 Attacker-Submitted Attached Data Injection]]** - メインプロンプト外の補助データ（ファイルアップロード等）内に悪意ある指示を含める技法

---

## 📊 **技法統計**

| カテゴリ | ファイル数 | 代表的な危険度 |
|---------|-----------|---------------|
| 状況操作・偽装 | 19個 | ★★★★☆ |
| 認知制御回避 | 18個 | ★★★☆☆ |
| 指示の変装・偽装 | 15個 | ★★★☆☆ |
| 回答の強制誘導 | 14個 | ★★★★☆ |
| 画像・音声攻撃 | 7個 | ★★★★★ |
| セッション内動的攻撃 | 6個 | ★★★★★ |
| データ汚染攻撃 | 6個 | ★★★★★ |
| システム処理混乱 | 4個 | ★★★★★ |
| 制限情報抽出 | 4個 | ★★★☆☆ |
| 第三者経由攻撃 | 3個 | ★★★★☆ |
| 段階的エスカレーション | 2個 | ★★★★★ |
| 検出回避・隠蔽 | 2個 | ★★★☆☆ |

**合計: 100個のメインファイル（PI-01〜PI-100完全網羅）**

---

## 📝 **更新履歴**

- **2025-08-08**: 完全体系化完了（PI-01〜PI-100全100個のメインファイル網羅）
- **技術進化追跡**: マルチモーダル攻撃・間接注入技法・セッション管理型攻撃の台頭を確認
- **分類体系**: 12カテゴリによる包括的分類完了

---

*このインデックスは学術研究と防御技術開発のためのものです。記載されている技法の悪用を目的とするものではありません。*