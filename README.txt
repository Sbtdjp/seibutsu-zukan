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

## v2で追加した機能
- 「和名がある生物だけ抽選」をONにすると、GBIFに日本語の和名（言語コード jpn / ja）が登録されている種だけを抽選します。
- 抽選カードには和名と学名を併記します。和名が見つからない場合は、通常モードでは学名を表示します。

## すでにGitHub Pagesで公開している場合の更新方法
1. ZIPを解凍します。
2. GitHubの対象リポジトリを開き、「Add file」→「Upload files」を選びます。
3. 解凍したフォルダ内のファイル5点（index.html、manifest.webmanifest、sw.js、icon.svg、icon-180.png）をアップロードします。
4. 同名ファイルを上書きする形でCommit changesします。
5. 1〜数分待ってからiPhoneのSafariで公開ページを再読み込みします。ホーム画面アプリに古い表示が残る場合は、Safariでページを開いて再読み込みしてからホーム画面アプリを起動してください。

## v3の変更
- 和名あり・画像ありを初期設定でONにしました。
- GBIF通信を最大3回まで再試行し、応答待ち時間を延長しました。
- 候補を少数ずつ並列確認し、1件ずつ通信する方式より待ち時間を短縮しました。
- 和名・画像の確認結果を端末内に保存し、同じ候補への再通信を減らします。
- 一部の通信に失敗しても抽選全体を即座に中断せず、候補と履歴を保持します。

## v3への更新
GitHub Pagesのリポジトリ直下にある同名ファイル5点を、ZIP内のファイルで上書きしてCommit changesしてください。更新後、Safariで公開ページを開いて再読み込みしてください。
