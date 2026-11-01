# ふたば家計簿

夫婦・家族で使える、ブラウザだけで動く家計簿アプリ(単一HTMLファイルのPWA)。

## 特徴
- `index.html` 1ファイルで完結(CSS/JS/アイコンを内蔵)
- データは端末の localStorage に保存。ログインすると Firebase(Auth + Firestore)で同期
- レシートOCR(Tesseract.js)対応
- ホーム画面に追加してアプリのように利用可能

## 使い方
- ローカル: `index.html` をブラウザで開く(この場合は同期なし・端末内保存のみ)
- 公開版: GitHub Pages の URL にアクセス

## GitHub Pages で公開する手順
1. GitHub で新しいリポジトリを作成(例: `futaba-kakeibo`)
2. このフォルダの中身を push
   ```sh
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<ユーザー名>/futaba-kakeibo.git
   git push -u origin main
   ```
3. リポジトリの **Settings → Pages → Source** を **GitHub Actions** に設定
4. Actions のデプロイ完了後、`https://<ユーザー名>.github.io/futaba-kakeibo/` で公開されます

## Firebase 設定(同期を使う場合)
- Firebase の Web API キーは公開前提の値で秘密ではありませんが、**Firestore セキュリティルールで本人のみアクセス可**にしてください(例: `users/{uid}/...` を `request.auth.uid == uid` のときだけ許可)。
- Firebase コンソール → Authentication → 設定 → **承認済みドメイン** に `<ユーザー名>.github.io` を追加してください。追加しないとログインできません。
- 設定されている Firebase プロジェクトは他のアプリと共有している可能性があります。ルールが他アプリと競合しないか確認してください。

## 外部リソース
Google Fonts / Firebase SDK(gstatic)/ Tesseract.js(jsDelivr)を CDN から読み込みます。

## ライセンス
MIT(`LICENSE` を参照)
