# 問診票OCR処理アプリ

問診票OCR処理アプリは、PDFまたはJPEG形式の問診票をアップロードし、Microsoft Azure Document Intelligence APIを使用してOCR処理を行い、抽出されたテキストをGemma LLMで整形してカルテ用フォーマットに変換するウェブアプリケーションです。

## 機能

- PDFまたはJPEG形式の問診票のアップロード（ドラッグ＆ドロップ対応）
- Microsoft Azure Document Intelligence APIを使用したOCR処理
- カスタムモデルIDの指定に対応
- 抽出テキストのGemma LLMによる整形（カルテ用フォーマット）
- APIキー設定と保存機能（ローカルストレージ使用）
- 処理結果のクリップボードコピー機能

## 技術スタック

- フロントエンド: Next.js + Tailwind CSS
- バックエンド: Next.js APIルート
- OCR処理: Azure Document Intelligence API
- テキスト整形: Gemma LLM（現在はモック実装）

## セットアップ手順

### 前提条件

- Node.js（バージョン16以上）
- npm（Node.jsに付属）
- Azure Document Intelligence APIのアクセスキーとエンドポイント

### ローカル開発環境のセットアップ

1. リポジトリをクローン
```bash
git clone https://github.com/yourusername/medical-ocr-app.git
cd medical-ocr-app
```

2. 依存関係のインストール
```bash
npm install
```

3. 環境変数の設定
`.env.example`ファイルを`.env.local`にコピーし、必要な情報を入力します。
```bash
cp .env.example .env.local
```
`.env.local`ファイルを編集して、Azure Document Intelligence APIキーとエンドポイントを設定します。

4. 開発サーバーの起動
```bash
npm run dev
```

5. ブラウザで[http://localhost:3000](http://localhost:3000)にアクセスしてアプリケーションを使用

### 使用方法

1. 「APIキー設定」セクションでAzure Document Intelligence APIキーとエンドポイントを設定
2. 必要に応じてカスタムモデルIDを入力（デフォルトは`prebuilt-layout`）
3. 「問診票のアップロード」セクションでPDFまたはJPEG形式のファイルをアップロード
4. 「OCR処理を開始」ボタンをクリックして処理を実行
5. 処理結果を確認し、必要に応じてクリップボードにコピー

## GitHubへのアップロード手順

1. GitHubでリポジトリを作成

2. ローカルリポジトリの初期化と設定
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/medical-ocr-app.git
git push -u origin main
```

## Renderでのデプロイ手順

### Renderアカウントの設定

1. [Render](https://render.com/)にサインアップまたはログイン
2. ダッシュボードから「New +」ボタンをクリック
3. 「Web Service」を選択

### GitHubリポジトリの接続

1. 「Connect a repository」セクションでGitHubアカウントを接続
2. medical-ocr-appリポジトリを選択

### デプロイ設定

1. 以下の設定を入力：
   - Name: medical-ocr-app（または任意の名前）
   - Environment: Node
   - Region: お好みのリージョン
   - Branch: main
   - Build Command: `npm install && npm run build`
   - Start Command: `npm start`

2. 環境変数の設定
   - 「Environment Variables」セクションで、`.env.example`に記載されている変数を追加
   - 実際のAzure APIキーとエンドポイントを設定

3. 「Create Web Service」ボタンをクリック

デプロイが完了すると、Renderが提供するURLでアプリケーションにアクセスできます。

## 注意事項

- Azure Document Intelligence APIを使用するには、有効なAPIキーとエンドポイントが必要です
- カスタムモデルを使用する場合は、事前にAzureポータルでモデルをトレーニングし、モデルIDを取得しておく必要があります
- 本番環境では、APIキーなどの機密情報を環境変数として設定し、クライアント側で保存しないようにセキュリティ対策を強化することをお勧めします

## ライセンス

MIT

## 謝辞

このプロジェクトは以下の技術を使用しています：
- [Next.js](https://nextjs.org)
- [Tailwind CSS](https://tailwindcss.com)
- [Microsoft Azure Document Intelligence](https://azure.microsoft.com/services/cognitive-services/document-intelligence/)
- [Gemma LLM](https://blog.google/technology/developers/gemma-open-models/)
