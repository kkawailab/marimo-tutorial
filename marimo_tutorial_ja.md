# marimo 初心者向けチュートリアル

このチュートリアルでは、marimoのインストールから基本的な使い方まで、ステップバイステップで学習します。

## 目次

1. [marimoとは](#marimoとは)
2. [インストール](#インストール)
3. [基本的なコマンド](#基本的なコマンド)
4. [最初のノートブックを作成](#最初のノートブックを作成)
5. [marimoの重要な概念](#marimoの重要な概念)
6. [インタラクティブな要素を使う](#インタラクティブな要素を使う)
7. [次のステップ](#次のステップ)

## marimoとは

marimoは、Pythonのためのリアクティブなノートブック環境です。Jupyter Notebookと似ていますが、以下の特徴があります:

- **リアクティブ**: セルが自動的に実行され、常に最新の状態を保ちます
- **インタラクティブ**: UIコンポーネントを簡単に作成できます
- **純粋なPython**: ノートブックは通常のPythonスクリプトとして保存されます
- **デプロイ可能**: ノートブックをWebアプリケーションとして簡単に公開できます

## インストール

### 前提条件

Python環境が必要です。仮想環境を使用することをお勧めします。

#### 仮想環境の作成と有効化

```bash
# 仮想環境を作成
python -m venv marimo-env

# 有効化 (macOS/Linux)
source marimo-env/bin/activate

# 有効化 (Windows)
marimo-env\Scripts\activate
```

### インストール方法

#### 最小限のインストール

最も簡単な方法はpipを使用します:

```bash
pip install marimo
```

他のパッケージマネージャーも使用できます:

```bash
# uvを使用 (高速でおすすめ)
uv add marimo

# condaを使用
conda install -c conda-forge marimo
```

#### 推奨インストール (より多くの機能)

SQL、AI補完、高度なプロットなどの追加機能が必要な場合:

```bash
pip install "marimo[recommended]"
```

このオプションには以下が含まれます:
- **duckdb**: SQLセルのサポート
- **altair**: データ可視化
- **polars**: 高速データ処理
- **openai**: AI機能
- **ruff**: コードフォーマット

### インストールの確認

インストールが成功したか確認します:

```bash
marimo tutorial intro
```

このコマンドで、marimoの入門チュートリアルが起動します。

## 基本的なコマンド

marimoはコマンドラインインターフェース(CLI)で操作します。主なコマンド:

### チュートリアルを実行

```bash
marimo tutorial intro
```

利用可能なすべてのチュートリアルを見る:

```bash
marimo tutorial --help
```

### ノートブックを編集

```bash
# 新しいノートブックを作成
marimo edit

# 特定のノートブックを編集
marimo edit my_notebook.py
```

### アプリケーションとして実行

```bash
marimo run my_notebook.py
```

このコマンドでノートブックをWebアプリケーションとして公開できます。コードは非表示・編集不可になります。

### Pythonスクリプトとして実行

```bash
python my_notebook.py
```

marimoノートブックは通常のPythonスクリプトなので、直接実行できます。

### 変換とエクスポート

Jupyterノートブックやスクリプトをmarimoに変換:

```bash
marimo convert notebook.ipynb -o notebook.py
marimo convert script.py -o notebook.py
```

他の形式にエクスポート:

```bash
marimo export html my_notebook.py -o output.html
marimo export ipynb my_notebook.py -o output.ipynb
```

## 最初のノートブックを作成

### ステップ 1: 新しいノートブックを作成

```bash
marimo edit hello_world.py
```

ブラウザが自動的に開き、marimoのエディタが表示されます。

### ステップ 2: 最初のセルを作成

エディタで「+ Add cell」をクリックするか、ショートカットキーを使用します。

最初のセルに以下を入力:

```python
import marimo as mo
```

### ステップ 3: テキストを表示

新しいセルを追加して:

```python
mo.md("# Hello, marimo!")
```

セルを実行すると、マークダウンがレンダリングされます。

### ステップ 4: 簡単な計算

新しいセルを追加:

```python
x = 10
y = 20
result = x + y
result
```

### ステップ 5: 結果を表示

新しいセルを追加:

```python
mo.md(f"計算結果: {x} + {y} = {result}")
```

ノートブックを保存すると、`hello_world.py`という通常のPythonファイルとして保存されます。

## marimoの重要な概念

### 1. リアクティブ実行

marimoの最も重要な特徴は**リアクティブ性**です。

```python
# セル 1
x = 5
```

```python
# セル 2
y = x * 2
```

```python
# セル 3
mo.md(f"yの値は {y} です")
```

セル1の`x`の値を変更すると、セル2とセル3が**自動的に再実行**されます。

### 2. 依存関係グラフ

marimoは各セルが:
- **参照する変数** (読み込む変数)
- **定義する変数** (作成する変数)

を分析し、依存関係グラフを作成します。

### 3. 変数の一意性

**重要**: 各変数は1つのセルでのみ定義できます。

```python
# ✅ 正しい例
# セル 1
x = 10

# セル 2
y = x + 5
```

```python
# ❌ 間違った例
# セル 1
x = 10

# セル 2
x = 20  # エラー: xはすでに定義されています
```

この制約により、隠れた状態のバグを防ぎます。

### 4. ミューテーションの制限

変数の変更はリアクティブ性をトリガーしません:

```python
# セル 1
my_list = [1, 2, 3]
```

```python
# セル 2
my_list.append(4)  # これは他のセルを再実行しません
```

**推奨**: 変数を変更する代わりに、新しい変数を作成します:

```python
# セル 2
new_list = my_list + [4]
```

## インタラクティブな要素を使う

marimoの強力な機能の1つは、簡単にインタラクティブなUIを作成できることです。

### スライダー

```python
import marimo as mo

slider = mo.ui.slider(start=0, stop=100, value=50, label="値を選択")
slider
```

### スライダーの値を使用

```python
mo.md(f"選択された値: **{slider.value}**")
```

スライダーを動かすと、この表示が自動的に更新されます！

### テキスト入力

```python
text_input = mo.ui.text(placeholder="名前を入力してください")
text_input
```

```python
mo.md(f"こんにちは、{text_input.value or '名無し'}さん！")
```

### チェックボックス

```python
checkbox = mo.ui.checkbox(label="同意します")
checkbox
```

```python
mo.md("✅ 同意しました" if checkbox.value else "⬜ 同意が必要です")
```

### ドロップダウン

```python
dropdown = mo.ui.dropdown(
    options=["Python", "JavaScript", "Rust", "Go"],
    value="Python",
    label="好きな言語を選択"
)
dropdown
```

```python
mo.md(f"あなたが選んだ言語: **{dropdown.value}**")
```

### データテーブル

```python
import pandas as pd

data = pd.DataFrame({
    "名前": ["太郎", "花子", "次郎"],
    "年齢": [25, 30, 35],
    "都市": ["東京", "大阪", "福岡"]
})

table = mo.ui.table(data)
table
```

### プロット (Matplotlib)

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.title("サインカーブ")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.grid(True)
plt.gca()
```

### インタラクティブなプロット例

```python
frequency = mo.ui.slider(start=1, stop=10, value=1, label="周波数")
frequency
```

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(frequency.value * x)

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.title(f"周波数 {frequency.value} のサインカーブ")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.grid(True)
plt.gca()
```

## 実践例: シンプルな計算機

すべてを組み合わせた例を見てみましょう:

```python
import marimo as mo
```

```python
mo.md("# シンプルな計算機")
```

```python
num1 = mo.ui.number(start=0, stop=1000, value=10, label="数値1")
num2 = mo.ui.number(start=0, stop=1000, value=5, label="数値2")

operation = mo.ui.dropdown(
    options={
        "加算": "+",
        "減算": "-",
        "乗算": "×",
        "除算": "÷"
    },
    value="+",
    label="演算"
)

mo.vstack([num1, num2, operation])
```

```python
if operation.value == "+":
    result = num1.value + num2.value
elif operation.value == "-":
    result = num1.value - num2.value
elif operation.value == "×":
    result = num1.value * num2.value
elif operation.value == "÷":
    result = num1.value / num2.value if num2.value != 0 else "エラー: 0で除算"

mo.md(f"## 結果: {num1.value} {operation.value} {num2.value} = **{result}**")
```

## よくある質問

### Q: Jupyter Notebookとの違いは？

A: 主な違い:
- **リアクティブ性**: marimoは自動的にセルを再実行します
- **変数の一意性**: 1つの変数は1つのセルでのみ定義可能
- **ファイル形式**: 純粋なPythonファイルとして保存されます
- **実行順序**: セルの位置ではなく、依存関係で決まります

### Q: Jupyterノートブックを移行できますか？

A: はい、簡単に変換できます:

```bash
marimo convert notebook.ipynb -o notebook.py
```

### Q: ノートブックを共有するには？

A: いくつかの方法があります:
1. `.py`ファイルを共有 (通常のPythonファイルです)
2. HTMLにエクスポート: `marimo export html notebook.py -o output.html`
3. Webアプリとしてデプロイ: `marimo run notebook.py`

### Q: セルが自動実行されないようにするには？

A: セルを無効化することができます。セルメニューから「Disable」を選択します。

## 次のステップ

marimoの基本を学んだので、以下を試してみましょう:

### 1. 組み込みチュートリアルを実行

```bash
marimo tutorial intro
marimo tutorial dataflow
marimo tutorial ui
marimo tutorial plots
```

### 2. ドキュメントを読む

公式ドキュメント: https://docs.marimo.io/

### 3. 実際のプロジェクトを作成

- データ分析ダッシュボード
- 機械学習の実験
- インタラクティブなレポート
- データ可視化アプリ

### 4. コミュニティに参加

- GitHub: https://github.com/marimo-team/marimo
- Discord: https://marimo.io/discord

## 便利なキーボードショートカット

- `Ctrl/Cmd + Enter`: セルを実行
- `Ctrl/Cmd + S`: ノートブックを保存
- `b`: 下に新しいセルを追加
- `a`: 上に新しいセルを追加
- `d d`: セルを削除
- `m`: セルをマークダウンに変更
- `c`: セルをコードに変更

## まとめ

このチュートリアルでは以下を学びました:

✅ marimoのインストール方法
✅ 基本的なコマンド
✅ ノートブックの作成と編集
✅ リアクティブ実行の仕組み
✅ インタラクティブなUI要素の使用
✅ 実践的な例

marimoを使って、よりインタラクティブで保守性の高いデータサイエンスプロジェクトを構築してください！

Happy coding! 🎉
