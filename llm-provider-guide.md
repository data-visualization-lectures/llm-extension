# AI - LLM Provider 定義ガイド
AI サービスおよびその設定内容を記録する LLM プロバイダーを管理するためのドキュメントです。

## 概要
このガイドでは、モデル、API キー、temperature、top-p、seed、max tokens などの主要パラメーターを指定して LLM プロバイダーを構成する方法を説明します。

/chat/completions エンドポイントに対応していない LLM を使いたい場合は [こちらのセクション](#llms-that-dont-support-the-chatcompletions-endpoint) を参照してください。

### [Ollama guide](https://github.com/sunilnatraj/llm-extension/blob/master/ollama-guide.md)
### [Groq guide](https://github.com/sunilnatraj/llm-extension/blob/master/groq-guide.md)
### [OpenRouter guide](https://github.com/sunilnatraj/llm-extension/blob/master/openrouter-guide.md)

## デモ動画

https://github.com/user-attachments/assets/e0c689de-3aff-4ece-8194-c483b4f17b5f


## 設定フィールド

| Field       | Description                                                                                                                                                       |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Label       | LLM プロバイダーに付けるユニークでわかりやすい名前。                                                                                                            |
| Server URL  | Chat completion API のエンドポイント。                                                                                                                            |
| Model       | 使用するモデル。プラットフォームでサポートされていることを確認してください。                                                                                     |
| API Key     | API へアクセスするための認証キー。ローカルサービスや認証不要のサービスならダミー値でも構いません。                                                              |
| Temperature | 応答のランダム性を制御します（1 = バランス、0 = 決定論的、1 より大きいと創造性が増す）。                                                                         |
| Top-P       | nucleus sampling を制御します（例: 0.8 なら累積確率 80% に含まれるトークンを候補にする）。                                                                       |
| Seed        | 再現性のある応答を得るための値（例: 32）。空欄だと応答は毎回変わります。                                                                                         |
| Max Tokens  | 応答で生成できる最大トークン数。大きくすると長い応答が可能ですが API 使用量も増えます。                                                                         |
| Wait Time   | リクエスト間で待機する時間。待機不要なら 0、2 秒待つなら 2000 などミリ秒で指定します。                                                                           |
 

## ボタンとアクション
| Button | Function |
|-------|----------|
| Help  | LLM プロバイダー設定のドキュメント／ガイドを開きます。 |
| Test Service | API キー・モデル・Server URL が正しいかをテスト呼び出しで確認します。 |
| Cancel | 変更を破棄してダイアログを閉じます。 |
| Save | 設定内容を保存します。 |

## Temperature - Top-P の設定と動作

| Temperature (T) | Top-P (P) | 出力への影響 | ユースケース |
|-------|-------------|-------|-------------|
| Low (T ≈ 0.2) | Low (P ≈ 0.5) | 高確率トークンのみをほぼ固定で使用し、変化がほとんどない決定的な応答。 | 数学、事実ベース、法律文書、コード生成など構造化出力に最適。 |
| Low (T ≈ 0.2) | High (P ≈ 0.95) | 主に決定的だが高信頼トークン内で多少の多様性を許容。 | カスタマーサポート、FAQ、厳密さが必要なチャットボット向け。 |
| Medium (T ≈ 0.7) | Low (P ≈ 0.5) | 多様性を抑えたバランスの取れた応答。 | 形式的な文章、製品説明、要約。 |
| Medium (T ≈ 0.7) | High (P ≈ 0.95) | 首尾一貫性と創造性のベストバランス。流暢さを保ちつつバリエーションも確保。 | ✅ チャット、一般会話、AI アシスタントに推奨のデフォルト。 |
| High (T ≈ 1.2) | Low (P ≈ 0.5) | 多少予測不能だがトップ候補は尊重。 | 物語、意見記事、クリエイティブライティング。 |
| High (T ≈ 1.2) | High (P ≈ 0.95) | 高い創造性と多様性。独自の応答を生成するが幻覚や脱線のリスクあり。 | 詩、フィクション、アイデア出し。 |
| Very High (T ≈ 2.0) | Low (P ≈ 0.5) | 混沌として非構造的だが高確率トークンからは選択。 | 極端な創造性が必要な場合以外は非推奨。 |
| Very High (T ≈ 2.0) | High (P ≈ 1.0) | 完全にランダムで意味を成さないことが多い。 | 実務用途では推奨されません。 |

## Top-P と Temperature の推奨デフォルト
| Use Case | Temperature | Top-P |
|-------|-------------|-------|
| General Chatbot / AI Assistant | 0.7 | 0.95 |
| Technical Writing / FAQs | 0.3 | 0.95 |
| Storytelling / Creative Writing | 1.2 | 0.9 |
| Code Generation / Logical Responses | 0.2 | 0.9 |
| Poetry / Idea Brainstorming | 1.5 | 0.95 |

## Seed

Seed は乱数生成器の固定された開始点です。言語モデルはトークン選択にランダムサンプリングを使うため、Seed を設定すると毎回同じ出力を得られます。

### 仕組み
1. 固定 Seed なし: 同じプロンプトでも実行するたびに異なる応答になります。
2. 固定 Seed あり（例: seed = 42）: 同じランダム経路をたどるため、毎回同じ応答になります。


## /chat/completions エンドポイントをサポートしない LLM について

もし Cohere や AI21、旧モデルのように /chat/completions をネイティブサポートしない LLM を使いたい場合は、[LiteLLM Proxy](https://docs.litellm.ai/docs/simple_proxy) サーバーで API インタラクションを標準化できます。
1. すべてのリクエストが対象モデルに関係なく /chat/completions エンドポイントを使用。
2. プロバイダー間でパラメーター（temperature、max_tokens など）を正規化。
3. 応答フォーマットを OpenAI 構造に合わせて標準化。
4. バックエンドでは LiteLLM が OpenAI 形式とプロバイダー固有形式の相互変換を処理します。
