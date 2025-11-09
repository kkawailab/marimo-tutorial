# marimo チュートリアル

marimoの初心者向け日本語チュートリアルリポジトリです。

## 概要

このリポジトリは、Pythonのリアクティブノートブック環境である[marimo](https://marimo.io/)の包括的な日本語チュートリアルを提供します。インストールから基本的な使い方、実践的な例まで、marimoを始めるために必要な情報が含まれています。

## marimoとは

marimoは、Jupyter Notebookに代わる新しいPythonノートブック環境です。以下の特徴があります:

- **リアクティブ**: セルが自動的に実行され、常に最新の状態を保ちます
- **インタラクティブ**: UIコンポーネントを簡単に作成できます
- **純粋なPython**: ノートブックは通常のPythonスクリプト(.py)として保存されます
- **デプロイ可能**: ノートブックをWebアプリケーションとして簡単に公開できます

## ドキュメント

### [marimo_tutorial_ja.md](marimo_tutorial_ja.md)

メインのチュートリアルドキュメントです。以下の内容が含まれます:

1. **インストール** - 仮想環境のセットアップと推奨インストール方法
2. **基本的なコマンド** - edit、run、convert、exportなどのCLI操作
3. **最初のノートブック作成** - ステップバイステップのガイド
4. **重要な概念** - リアクティブ実行、依存関係グラフ、変数の一意性
5. **インタラクティブな要素** - スライダー、入力フォーム、プロットなど
6. **実践例** - シンプルな計算機アプリの実装
7. **FAQ** - よくある質問とトラブルシューティング
8. **次のステップ** - さらなる学習のためのリソース

## クイックスタート

### 1. 仮想環境の作成

```bash
python -m venv marimo-env
source marimo-env/bin/activate  # macOS/Linux
# marimo-env\Scripts\activate  # Windows
```

### 2. marimoのインストール

```bash
# 最小限のインストール
pip install marimo

# 推奨インストール (SQL、AI、高度なプロット機能を含む)
pip install "marimo[recommended]"
```

### 3. チュートリアルを実行

```bash
# marimoの組み込みチュートリアルを起動
marimo tutorial intro

# 新しいノートブックを作成
marimo edit my_notebook.py
```

## リンク

- [marimo公式サイト](https://marimo.io/)
- [marimo公式ドキュメント](https://docs.marimo.io/)
- [marimoリポジトリ](https://github.com/marimo-team/marimo)
- [marimoコミュニティDiscord](https://marimo.io/discord)

## ライセンス

このチュートリアルはMITライセンスの下で公開されています。

## 貢献

改善提案やバグ報告は、Issueやプルリクエストでお知らせください。

## 更新履歴

### 2025-11-09

- **初回リリース**
  - marimo日本語チュートリアル (marimo_tutorial_ja.md) を追加
  - インストールから実践例までの包括的なガイド
  - リアクティブ実行の概念説明
  - インタラクティブUI要素のサンプルコード
  - 計算機アプリの実装例
  - CLAUDE.md (Claude Code用のリポジトリガイダンス) を追加
  - README.md を追加
