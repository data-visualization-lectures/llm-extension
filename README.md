OpenRefine 用 AI Extension 
=========================

OpenRefine AI Extension は、最新の大規模言語モデルの力と OpenRefine の強力なデータ変換機能をつなぎます。チャット補完 API エンドポイントに対応したあらゆる LLM プロバイダーを利用できるため、AI を使ったデータ整形・強化・分析を OpenRefine のワークフローに直接組み込めます。詳しくは、このリポジトリにある [AI Column Extraction](llm-prompt-guide.md) と [Provider Setup](llm-provider-guide.md) ガイドを参照してください。

## 目的
この拡張機能はデータ処理パイプラインで以下の用途を担います。

1. インテリジェントなデータクリーニング: ルールベースを超える文脈対応のクリーニング操作を LLM に提案・実行させます。
2. セマンティックな拡張: 既存の内容に基づいて追加属性やメタデータを生成し、データセットを拡充します。
3. 自然言語による変換: 複雑なデータ変換を平易な英語で記述できます。
4. 異常検知: AI 解析でデータ中の異常パターンや外れ値を特定します。
5. コンテンツ生成: 文脈に即した合成データでデータセットの欠損を補います。

この拡張機能は **OpenRefine 3.8.7 以降** で動作します。


### OpenRefine へのインストール

[最新リリース](https://github.com/sunilnatraj/llm-extension/releases) の .zip ファイルをダウンロードします。
zip を展開し、生成されたフォルダーを OpenRefine の extensions フォルダーに配置します。インストール手順の詳細は [OpenRefine ユーザーマニュアル](https://openrefine.dataviz.jp/docs/manual/installing#installing-extensions) を参照してください。

インストールが正しく完了すると、プロジェクトを開いた際に Extensions バーに AI メニューが表示されます。
