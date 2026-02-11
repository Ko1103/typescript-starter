# AGENTS.md

## プロジェクト概要

毎日英単語を学習するための Web アプリケーション（Next.js App Router）。

## 技術スタック・バージョン

| ツール                 | バージョン | 用途                           |
| ---------------------- | ---------- | ------------------------------ |
| Node.js                | v24        | ランタイム (fnm で管理)        |
| pnpm                   | v10        | パッケージマネージャー         |
| Next.js                | 16.1.6     | フレームワーク (App Router)    |
| React                  | 19.2.4     | UI ライブラリ                  |
| TypeScript             | ^5         | 型付き言語                     |
| Tailwind CSS           | ^4         | ユーティリティ CSS             |
| shadcn/ui              | -          | UI コンポーネント              |
| ESLint                 | ^9         | リンター（flat config 形式）   |
| eslint-config-next     | 16.1.6     | Next.js 向け ESLint ルール     |
| eslint-config-prettier | ^10        | Prettier との競合回避          |
| Prettier               | ^3.8       | コードフォーマッター           |
| husky                  | ^9         | Git hooks 管理                 |
| lint-staged            | ^16        | ステージファイルの lint/format |

## コマンド一覧

```bash
pnpm dev            # 開発サーバー起動 (http://localhost:3000)
pnpm build          # プロダクションビルド
pnpm start          # プロダクションサーバー起動
pnpm lint           # ESLint 実行
pnpm format         # Prettier で全ファイルをフォーマット
pnpm format:check   # フォーマット差分チェック（CI 向け）
```

## Git hooks

- **pre-commit** (`lint-staged` 経由):
  - `*.{ts,tsx}` → `eslint --fix` + `prettier --write`
  - `*.{json,css,md}` → `prettier --write`

## ディレクトリ構成

```text
.
├── app/                  # Next.js App Router（ページ・レイアウト）
│   ├── layout.tsx        #   ルートレイアウト
│   ├── page.tsx          #   トップページ
│   ├── globals.css       #   グローバル CSS (Tailwind)
│   └── favicon.ico
├── public/               # 静的アセット
├── .husky/               # Git hooks (pre-commit)
├── .vscode/              # VSCode 設定（formatter, 推奨拡張機能）
├── eslint.config.mjs     # ESLint 設定 (flat config)
├── .prettierrc           # Prettier 設定
├── tsconfig.json         # TypeScript 設定
├── next.config.ts        # Next.js 設定
├── postcss.config.mjs    # PostCSS 設定 (Tailwind CSS)
├── package.json
└── pnpm-lock.yaml
```

## コーディング規約

- **言語**: TypeScript（strict モード有効）
- **パスエイリアス**: `@/*` → プロジェクトルート（例: `@/app/page`）
- **フォーマット**: Prettier（セミコロンあり / シングルクォート / 末尾カンマ / 80 文字折り返し）
- **リント**: ESLint flat config + Next.js core-web-vitals + TypeScript ルール
- **スタイリング**: Tailwind CSS ユーティリティクラスを使用。UI コンポーネントは shadcn/ui を利用
