# OpenRouter
[OpenRouter](openrouter.ai) は OpenAI、Google、Anthropic、Mistral など複数プロバイダーの AI モデルへ統一 API でアクセスできるプラットフォームです。単一の API キーと OpenAI 互換の標準化 API で、さまざまなモデルとやり取りできます。

## 対応 LLM モデル
[サポートされている LLM の一覧](https://openrouter.ai/models)

## レート制限
[ドキュメントを参照](https://openrouter.ai/docs/api-reference/limits)

## API キー
1. openrouter.ai にログイン後、API キーを取得します。
2. Create API Key - https://openrouter.ai/settings/keys >> Create API Key >> <your key> を保存します。
3. アカウント管理 - https://openrouter.ai/settings/preferences
4. クレジット確認 - https://openrouter.ai/settings/credits 
5. クイックスタートガイド - https://openrouter.ai/docs/quickstart

## OpenAI 互換性
OpenRouter は OpenAI と完全互換で、多くのパラメーターに対応しています。チャット補完に関する詳細は https://openrouter.ai/docs/api-reference/chat-completion を参照してください。

# AI プラグイン向け OpenRouter 設定（プラグイン V0.1.2／OpenRefine 3.9+）

| Attribute  | Value |
|-------------|------------|
 | apiURL |  https://openrouter.ai/api/v1/chat/completions | 
 | modelName | モデル名を設定 |
 | apiKey | <apiKey> |
 | waittime | 5000 | 

全属性の詳細はセットアップガイドを参照してください。

### NB: 同じ API キーを使いながら、異なるモデルで複数の OpenRouter インスタンスを作成できます。インスタンスラベル（例: OpenRouter-DeepSeek）を変更し、使用したいモデル名（例: deepseek/deepseek-v3-base:free）を指定してください。他の設定値は必要に応じて調整するか、既存のままでも問題ありません。

![image](https://github.com/user-attachments/assets/6e2d9023-a450-43b1-9233-b63eaeb84dab)
