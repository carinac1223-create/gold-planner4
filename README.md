# 目標理財規劃 Goal Finance Planner

純靜態網頁（單一 `index.html`），無需建置步驟。

## 專案結構

```
goal-finance-planner/
├── public/index.html          # 網站本體
├── wrangler.jsonc             # Cloudflare 設定
├── .github/workflows/deploy.yml  # 選用：GitHub Actions 自動部署
├── .gitignore
└── README.md
```

## 1. 建立 GitHub 儲存庫

```bash
cd goal-finance-planner
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<你的帳號>/goal-finance-planner.git
git push -u origin main
```

（需先在 GitHub 建立同名的空儲存庫。）

## 2. 部署到 Cloudflare Pages

### 方法 A：Cloudflare 連結 GitHub（最簡單）

1. Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git
2. 選擇此儲存庫
3. Framework preset：None；Build command：留空；Build output directory：`public`
4. Save and Deploy，完成後取得 `xxx.pages.dev` 網址

> 使用方法 A 時請刪除 `.github/workflows/deploy.yml`。

### 方法 B：GitHub Actions 自動部署

1. 先在 Cloudflare 建立 Pages 專案 `goal-finance-planner`（Direct Upload）
2. 在 GitHub 儲存庫設定 Secrets：`CLOUDFLARE_API_TOKEN`、`CLOUDFLARE_ACCOUNT_ID`
3. 之後每次 push 到 `main` 就會自動部署

### 方法 C：指令列

```bash
npx wrangler pages deploy public --project-name=goal-finance-planner
```

## 本機預覽

```bash
npx wrangler pages dev public
```
