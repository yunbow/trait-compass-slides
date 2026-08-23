# trait-compass-slides へのコントリビューション

ご協力ありがとうございます。trait-compass-slides（Trait Compass 提出用プレゼン資料）への貢献を歓迎します。

## 貢献の方法

### 不具合報告・改善提案

- [GitHub Issues](https://github.com/yunbow/trait-compass-slides/issues) をご利用ください。
- 表示崩れなどの不具合は、再現手順・期待する動作・実際の動作・確認した環境を可能な範囲で記載してください。
- 文言・数値の誤りやアクセシビリティについての改善提案も歓迎します。

### Pull Request

1. リポジトリを Fork します。
2. 作業用ブランチを作成します。
3. 変更を実施します。
4. 変更内容が分かるコミットメッセージを付けてコミットします。
5. Pull Request を作成します。

### 開発環境のセットアップ

```bash
cd app
npm install
npm run dev
```

### 変更前の確認

Pull Request を送る前に、以下が成功することを確認してください。

```bash
cd app
npm run build
```

`npm run build` は Slidev のビルドを実行し、`app/dist` に GitHub Pages 用の公開ファイルを生成します（デプロイは GitHub Actions が `app/dist` を Pages artifact としてアップロードして行います）。ビルド成果物はリポジトリにコミットしないでください。

提出物（PDF/PPTX/PNG）に関わる変更を行った場合は、`npm run export` / `export:pptx` / `export:png` で書き出しが崩れないことも確認してください。

### コンテンツ

- 文言・統計値は一次情報（[yunbow/trait-compass](https://github.com/yunbow/trait-compass) の確定内容）と一致させてください。数値・出典を独自に変更しないでください。
- レイアウトを崩さない修正方法は [README.md](./README.md) の「レイアウトを崩さず修正する」を参照してください。
- 外部フォント、アナリティクス、トラッキングコードは追加しないでください。

## 行動規範

敬意を持って、建設的に、誰もが参加しやすい態度でご協力ください。
