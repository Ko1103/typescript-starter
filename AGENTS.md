# For Coding Agents

## Commands

```bash
pnpm dev            # dev server (http://localhost:3000)
pnpm build          # production build
pnpm start          # up prod server
pnpm lint
pnpm format
pnpm format:check   # format check for CI
```

## Git hooks

- **pre-commit** (`lint-staged` 経由):
  - `*.{ts,tsx}` → `eslint --fix` + `prettier --write`
  - `*.{json,css,md}` → `prettier --write`

## Directory Structure

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
