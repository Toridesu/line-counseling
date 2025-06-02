# LINE カウンセリングアプリ

**LINE Messaging API （Bot）を活用した Web アプリケーション開発について学習。**
**Next.js と LINE 公式アカウントを連携させる方法や、LIFF を用いた LINE 内での予約フローの構築**

このプロジェクトでは、架空のプログラミングスクールを想定して、コーポレートサイトを構築しました。

公式 LINE を「友だち追加」することができ、
LINE 上、Web 上の両方で、無料カウンセリングの日時を予約できるシステムを実装しました。

## ✨ 主な機能 (想定)
- **ランディングページ:** プログラミングスクールの特徴を紹介します。
- **公式 LINE 友達追加:** QR コードまたはボタンから LINE 公式アカウントを友達追加できます。
- **無料カウンセリング予約:**
  - Web サイト上と LINE 上の両方から予約フォームにアクセスできます。
  - LINE 上で、予約の確認・キャンセルができます。

## 🚀 技術スタック

- **フレームワーク:** Next.js (App Router, Turbopack)
- **言語:** TypeScript
- **UI:** React
- **スタイリング:** Tailwind CSS
- **UI コンポーネント:** shadcn/ui (lucide-react, class-variance-authority, clsx, tailwind-merge を利用)
- **LINE 連携:** @line/bot-sdk, @line/liff
- **データベース:** Neon (Serverless Postgres) via `@neondatabase/serverless` and `postgres`

## 🛠️ 開発環境のセットアップ

1. **リポジトリをクローン:**
   ```bash
   git clone https://github.com/あなたのユーザー名/line-counseling.git
   cd line-counseling
   ```
2. **依存パッケージのインストール:**
   ```bash
   npm install
   # または
   # yarn install
   # または
   # pnpm install
   ```
3. **開発サーバーの起動:**
   ```bash
   npm run dev
   # または
   # yarn dev
   # または
   # pnpm dev
   ```
   ブラウザで `http://localhost:3000` を開きます。

## 📁 プロジェクト構成 (src ディレクトリ)

```
src
├── app/            # Next.js App Routerのルーティングとページコンポーネント
│   ├── (root)/     # ルートパス ("/") に対応するページ、レイアウト、グローバルCSSなど
│   ├── api/          # APIルート (バックエンド処理)
│   │   ├── webhook/      # LINE Messaging APIのWebhook処理関連
│   │   └── reservations/ # 予約関連API (例: LINE経由の予約処理)
│   ├── liff/         # LIFF (LINE Front-end Framework) アプリケーションのページ群
│   │   └── reserve/    # 予約用LIFFページ関連
│   └── ...           # その他、機能ごとのルーティングディレクトリ
├── components/     # 再利用可能なUIコンポーネント群
│   ├── ui/           # shadcn/ui から導入したベースUIコンポーネント (Button, Cardなど)
│   └── *.tsx         # プロジェクト固有のカスタムコンポーネント (Header, Pricingなど)
├── lib/            # 外部ライブラリの設定やユーティリティ、コアロジック
│   ├── line-bot/     # LINE Bot関連のクライアント設定やメッセージ定義
│   ├── liff/         # LIFFアプリ関連のユーティリティ関数
│   ├── neon/         # Neonデータベース (PostgreSQL) との連携処理
│   └── utils.ts      # shadcn/ui のユーティリティ関数 (cnなど)
├── actions/        # Next.js Server Actions (フォーム送信処理など)
├── constants/      # アプリケーション全体で使われる定数 (現状未作成、必要に応じて追加)
├── types/          # TypeScriptの型定義 (現状未作成、必要に応じて追加)
└── utils/          # 汎用的なユーティリティ関数 (現状未作成、必要に応じて追加)
```

---
