# GROQ
[Groq Console](console.groq.com) は、Groq ハードウェア上で動作するオープンソース AI モデルと対話できるオンラインインターフェースです。提供される機能は以下のとおりです。
1. LLM へのアクセス: Groq のハードウェア向けに最適化されたモデルに対してプロンプトを実行できます。
2. API 連携: Groq の AI 処理機能を自分のアプリケーションへ統合できます。

## 対応 LLM モデル
[サポートされている LLM の一覧](https://console.groq.com/docs/models)

## レート制限
1. [ドキュメント参照](https://console.groq.com/docs/rate-limits)
2. フリーティアでの制限値 - https://console.groq.com/dashboard/limits
3. 使用状況の確認 - https://console.groq.com/dashboard/usage

## API キー
1. console.groq.com にログイン後、API キーを取得します。
2. Create API Key >> https://console.groq.com/keys >> API キーを保存します。
3. ダッシュボード - https://console.groq.com/dashboard/

## OpenAI 互換性
Groq API は OpenAI のクライアントライブラリとほぼ互換となるよう設計されているため、既存アプリを最小限の設定変更で Groq 上に構成し、その高速な推論を体験できます。OpenAI のクライアントライブラリで Groq を使用する際は base_url を https://api.groq.com/openai/v1 に設定してください。

# AI プラグイン向け Groq 設定（プラグイン V0.1.2／OpenRefine 3.9+）

| Attribute  | Value |
|-------------|------------|
 | apiURL |  https://api.groq.com/openai/v1/chat/completions | 
 | modelName | モデル名を設定 |
 | apiKey | <apiKey> |
 | waittime | 5000 | 

全属性の詳細はセットアップガイドを参照してください。

### NB: 同じ API キーを使いながらモデルを変えて複数の Groq インスタンスを作成できます。インスタンスのラベル（例: Groq-DeepSeek）とモデル名（例: deepseek-r1-distill-llama-70b）を変更すればよく、その他の設定値は必要に応じて調整するか既存のままでも構いません。

![image](https://github.com/user-attachments/assets/a8427a50-1de5-4f38-b08a-7c2633813012)
