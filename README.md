# 単価比較＆ベスト記録アプリ

買い物中に2つの商品の単価（1g・1ml・1m・1個・1枚・1ロールあたり）を比べて、品目ごとに一番お得だった商品を記録しておくアプリです。
iPhone / iPad の Safari で開いて「ホーム画面に追加」して使います。オフラインでも動き、データは端末内（localStorage）だけに保存されます。

## ファイル

| ファイル | 役割 |
|---|---|
| `index.html` | アプリ本体（画面・デザイン・処理すべて） |
| `manifest.json` | ホーム画面に追加したときの名前・アイコンなど |
| `service-worker.js` | オフラインで動かすためのキャッシュ |
| `icon-192.png` / `icon-512.png` / `apple-touch-icon.png` | アイコン |

## パソコンで動作確認する

```sh
python3 -m http.server 8000
```
ブラウザで http://localhost:8000/ を開きます（`index.html` を直接ダブルクリックしても動きますが、オフライン機能は働きません）。

## GitHub Pages で公開する

1. GitHub のリポジトリ画面で **Settings** → 左メニューの **Pages** を開く
2. **Build and deployment** の **Source** を「Deploy from a branch」にする
3. **Branch** で公開したいブランチ（例：`main`）と `/ (root)` を選び **Save**
4. 1〜2分待つと、画面上部に `https://<ユーザー名>.github.io/app_setsuyaku/` が表示される

## iPhone のホーム画面に追加する

1. iPhone の **Safari** で上のURLを開く（Chromeなどでは不可）
2. 画面下の **共有ボタン**（□に↑）をタップ
3. **ホーム画面に追加** → **追加**
4. ホーム画面のアイコンから起動。一度開けば、以後は機内モードでも使えます

## アプリを更新したとき

`service-worker.js` の `CACHE_NAME`（例：`tanka-v1` → `tanka-v2`）を書き換えてから公開してください。
iPhone 側ではアプリを1〜2回開き直すと新しい版に切り替わります。

## 注意

- データは端末のSafari内だけに保存されます。Safariの「履歴とWebサイトデータを消去」をするとデータも消えます。
- 「ホーム画面のアプリ」と「Safariで開いたページ」はデータが別々です。普段はホーム画面のアイコンから使ってください。
