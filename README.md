# 物件撮影フロー PWA

## ファイル構成
```
pwa-shoot/
├── index.html      ← メインアプリ（React + IndexedDB永続化）
├── manifest.json   ← PWAマニフェスト
├── sw.js           ← Service Worker（オフラインキャッシュ）
├── icon-192.png    ← アプリアイコン 192x192
├── icon-512.png    ← アプリアイコン 512x512
└── README.md       ← このファイル
```

## GitHub Pages デプロイ手順

### 1. リポジトリ作成
```bash
cd pwa-shoot
git init
git add .
git commit -m "初回デプロイ: 物件撮影フローPWA"
```

### 2. GitHubにプッシュ
```bash
gh repo create shoot-flow --public --source=. --push
# または
git remote add origin https://github.com/YOUR_USERNAME/shoot-flow.git
git branch -M main
git push -u origin main
```

### 3. GitHub Pages 有効化
- リポジトリ → Settings → Pages
- Source: 「Deploy from a branch」
- Branch: 「main」 / 「/ (root)」
- Save

### 4. 公開URL
`https://YOUR_USERNAME.github.io/shoot-flow/`

## スマホでホーム画面に追加

### iPhone (Safari)
1. 上記URLをSafariで開く
2. 共有ボタン（□↑）をタップ
3. 「ホーム画面に追加」を選択

### Android (Chrome)
1. 上記URLをChromeで開く
2. アドレスバーの「インストール」バナー or メニュー →「ホーム画面に追加」

## 技術仕様
- **データ保存**: IndexedDB（ブラウザ内永続化、リロードしてもデータ保持）
- **オフライン対応**: Service Workerによるアプリキャッシュ
- **カメラ**: getUserMedia API（HTTPS必須）
- **共有**: Web Share API（スマホのネイティブ共有シート）
- **認証**: アプリ内認証（初期: admin/admin）
