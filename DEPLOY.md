# PRISM CUP 2026 — Cloudflare Pages デプロイ手順

## フォルダ構成
```
prismcup-deploy/
├── index.html      ← prismcup-master.html（メインページ）
├── wrangler.toml   ← Cloudflare設定ファイル
└── DEPLOY.md       ← この手順書
```

---

## 初回デプロイ（Cloudflare Pagesプロジェクト作成）

### 前提条件
- Cloudflareアカウントがあること
- Node.js がインストールされていること

### 手順

**① wrangler をインストール（初回のみ）**
```bash
npm install -g wrangler
```

**② Cloudflareにログイン（初回のみ）**
```bash
npx wrangler login
```
→ ブラウザが開くので承認する

**③ このフォルダに移動してデプロイ**
```bash
cd prismcup-deploy
npx wrangler pages deploy . --project-name prismcup2026
```

→ 初回は新しいPagesプロジェクトが自動作成される  
→ デプロイ完了後に URL が表示される（例: `https://prismcup2026.pages.dev`）

---

## 2回目以降の更新デプロイ

```bash
cd prismcup-deploy
npx wrangler pages deploy . --project-name prismcup2026
```

---

## カスタムドメインを設定したい場合

1. Cloudflareダッシュボード → Workers & Pages → prismcup2026
2. 「カスタムドメイン」タブ → ドメインを追加

---

## 注意事項
- `index.html` = メインページ（prismcup-master.htmlのコピー）
- HTMLを更新したら `index.html` を差し替えて再デプロイするだけ
