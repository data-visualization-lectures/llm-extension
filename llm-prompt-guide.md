# AI Column Extraction 機能
AI を活用したテキスト抽出および変換機能のドキュメントです。

## 概要
AI Column Extraction 機能を使うと、既存のテキストデータを AI 言語モデルで処理し、新しい列を生成できます。ソーステキストから特定情報を抽出したり、内容を変換したり、洞察を得たりできます。

## デモ動画

https://github.com/user-attachments/assets/aed38ce9-d884-4146-a82e-a761a13fed20

## 設定

### 基本設定
1. Column: 新しい列を追加するか既存列を更新するかを選択し、AI の出力結果を格納する列名を指定します。
2. LLM Provider: 事前設定済みの AI プロバイダー（モデル、サーバー URL、Temperature、Max Tokens を含む）を選択します。
3. Response Format: 出力形式を選択します。

| Response format  | Description |
|-------------|------------|
 | `Text |  プレーンテキストでの応答 | 
 | `JSON Schema |  定義済みスキーマに従う構造化レスポンス | 
 | `JSON Object |  自由形式の JSON レスポンス | 

### 入力設定

1. Description: 求める抽出や変換内容について、AI モデル向けに詳細な指示を記述します。
2. JSON Schema（任意）: Response Format が JSON Schema の場合に必須。出力の構造とバリデーションルールを定義します。

#### JSON Schema 生成ツール
1. [Liquid Technologies JSON to Schema converter](https://www.liquid-technologies.com/online-json-to-schema-converter)
2. [jsonschema.net](http://www.jsonschema.net)
3. [easy-json-schema.github.io](https://easy-json-schema.github.io)

注: 一部は手作業で編集が必要な場合があります。下記サンプルの JSON スキーマを参照してください。

### プレビュー機能

最初の 1 行を使ってサンプル処理を表示します。表示内容:
1. Input Value: 元の列から取得したテキスト。
2. Response: 設定内容に基づいて AI が生成した結果。

全データセットを処理する前に設定内容を検証できます。

### History

1. プロジェクトと最新使用順で並ぶ、過去に使ったプロンプト一覧を表示します。
2. 最大 100 件まで保持します。
3. 各エントリにアクションボタン、ソース、LLM プロバイダー、レスポンス形式、プロンプト内容が含まれます。
4. プロンプトをスター（お気に入り登録）したり再利用したりできます。

### Starred

1. お気に入りに登録したプロンプトのみを表示します。
2. 各エントリは History と同じ情報を示します。
3. スターを外す（お気に入り解除）か、プロンプトを再利用できます。

## サンプル

### Text レスポンス例
| ユースケース | 指示 |
|-------------|------------|
| 基本的な要約 | 入力テキストを 1 文で要約する |
| 言語翻訳 | テキストをドイツ語へ翻訳する |

### JSON Schema 例
| ユースケース | 指示 | JSON Schema |
|-------------|------------|------------|
| 人物情報抽出 | コンテンツに登場する人物の詳細を JSON 形式で抽出する | ``` { "name": "individual_schema", "schema": { "type": "object", "properties": { "name": { "type": "string", "description": "The name of the individual." }, "dateofbirth": { "type": "string", "description": "The date of birth of the individual." }, "placeofbirth": { "type": "string", "description": "The place where the individual was born." }, "dateofdeath": { "type": "string", "description": "The date of death of the individual." }, "placeofdeath": { "type": "string", "description": "The place where the individual died." } }, "required": [ "name", "dateofbirth", "placeofbirth", "dateofdeath", "placeofdeath" ], "additionalProperties": false }, "strict": true }``` |

### JSON オブジェクト例

| ユースケース | 指示 |
|-------------|------------|
| コンテンツ分類 | コンテンツを分類し主要エンティティを抽出する。レスポンスは JSON 形式とする |

## ユースケース

### コンテンツ変換

1. Summarization（要約）
2. Translation（翻訳）
3. Style conversion（文体変換）
4. Format standardization（書式標準化）


### 情報抽出

1. Entity recognition（エンティティ認識）
2. Key fact extraction（主要事実の抽出）
3. Timeline creation（タイムライン作成）
4. Relationship mapping（関係マッピング）


### コンテンツ分析

1. Sentiment analysis（感情分析）
2. Theme identification（テーマ特定）
3. Category classification（カテゴリ分類）
4. Key concept extraction（主要概念抽出）
