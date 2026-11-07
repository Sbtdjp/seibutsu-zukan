# 生物ランダム図鑑（iPhone向けPWA）

## iPhoneで使うまで
このフォルダの中身をHTTPS対応の静的ホスティングへ公開してください。手軽な方法はGitHub Pagesです。

1. GitHubにログインし、新しいPublicリポジトリを作成（例: `seibutsu-zukan`）。
2. このZIPを解凍し、`index.html`、`manifest.webmanifest`、`sw.js`、`icon.svg`、`icon-180.png`をリポジトリ直下へアップロード。
3. GitHubのリポジトリで Settings → Pages を開く。
4. Build and deployment の Source を「Deploy from a branch」、Branchを `main`、Folderを `/ (root)` にして Save。
5. 公開された `https://ユーザー名.github.io/seibutsu-zukan/` をiPhoneのSafariで開く。
6. Safariの共有ボタン →「ホーム画面に追加」→「追加」。
7. ホーム画面の「生物図鑑」アイコンから起動。

## 重要
- 生物データと画像の取得にはインターネット接続が必要です。
- この試作版はGBIF Species APIの検索ページング上限（offset 99,000付近）を考慮し、取得可能な候補範囲からランダム抽出します。GBIF登録種数すべてからの完全な一様抽選ではありません。
- 「画像がある生物だけ抽選」は、GBIFのOccurrence APIでStillImage付き記録が見つかる種に限定します。画像URLが後から無効になる場合もあるため、すべての画像表示を保証するものではありません。
- 画像付き種の確認には追加API通信が発生するため、ONにすると抽選が遅くなります。
- 履歴・設定は同じiPhone・同じブラウザ内のlocalStorageに保存します。SafariのWebサイトデータを消去すると消えます。
- このPWAはホーム画面起動に対応するWebアプリです。App Store配布用のネイティブアプリではありません。

## ファイル
- index.html: アプリ本体
- manifest.webmanifest: ホーム画面アプリ設定
- sw.js: アプリ画面のキャッシュ
- icon.svg: アイコン
