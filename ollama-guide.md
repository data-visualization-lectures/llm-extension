![ollama](https://github.com/user-attachments/assets/ea18144e-878f-4b8d-9b71-011e738516c9)
# Ollama

Ollama は、オープンソースの大規模言語モデル (LLM) をローカルで実行し対話できるツールです。

## インストール
[インストール手順](https://docs.ollama.com/getting-started/installation)

## 対応 LLM モデル
[サポートされている LLM 一覧](https://ollama.com/library)

## LLM モデルのインストール
[LLM モデルをインストールする手順](https://docs.ollama.com/reference/models)

## コマンドリファレンス

| Command  | Description |
|-------------|------------|
 | ollama list |  PC 上の LLM モデル一覧を表示 | 
 | ollama show <model name> |  モデル情報を表示 | 
 | ollama ps |  現在ロードされているモデルを一覧表示 | 
 | ollama run <model> |  指定モデルを実行し、対話可能な状態にする |
 | ollama stop <model name> | 実行中のモデルを停止 |

## OpenAI 互換性
Ollama は一部の OpenAI API 機能を限定的にサポートしており、既存アプリケーションとの連携が可能です。[詳細はこちら](https://docs.ollama.com/api/openai-compatibility)
1. OpenAI-Compatible API のエンドポイント仕様と例を同ページで確認できます。
2. Chat completion endpoint: http://localhost:11434/v1/chat/completions

# AI プラグイン向け Ollama 設定（プラグイン V0.1.2／OpenRefine 3.9+）

| Attribute  | Value |
|-------------|------------|
 | apiURL |  http://localhost:11434/v1/chat/completions | 
 | modelName | 使用したいモデル名を設定（例: llama3.1:8b） |
 | apiKey | 1234 |
 | waittime | 1000 | 

全属性の詳細はセットアップガイドを参照してください。

![image](https://github.com/user-attachments/assets/6e0fae2d-7410-42c4-a6df-48475a98a176)
