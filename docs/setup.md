# Setup

## 推奨セットアップ順

このシステムは、次の順で導入すると詰まりにくいです。

1. Raspberry Pi 側をセットアップする
2. `index.png` と `index.version` の HTTP 配信を確認する
3. M5PaperS3 側へ Wi‑Fi と配信先 URL を設定する
4. M5PaperS3 の表示とページ遷移を確認する
5. 定期更新、優先先読み、`NEW / READ` を確認する

## 1. Raspberry Pi 側

最低限やること:

- Python 仮想環境を作る
- `pillow` と `feedparser` を入れる
- 必要フォントを `fonts/` へ置く
- `make_pages_png.py` で画像生成できることを確認する
- `http.server` で `index.png` を配信できることを確認する
- `systemd/` の unit を `~/.config/systemd/user/` へ配置する

## 2. M5PaperS3 側

最低限やること:

- `config.h` に Wi‑Fi 設定を書く
- Arduino IDE または `arduino-cli` でビルドする
- M5PaperS3 に書き込む
- `index` が表示されることを確認する
- タップ / スワイプでページ遷移することを確認する

## 3. 連携確認

Raspberry Pi 側で確認:

- `curl -I http://127.0.0.1:8010/index.png`
- `systemctl --user status m5news-http.service`
- `systemctl --user status m5news-generate.timer`

M5 側で確認:

- `index` 表示
- 詳細ページ遷移
- 定期更新
- 右上 `NEW / READ`

## 更新時の作業

### Raspberry Pi 側を修正した場合

1. Mac 上の `m5papers3-news-server` で編集
2. commit / push
3. Raspberry Pi 上で `git pull`
4. 必要なら service / timer を再起動

### M5 側を修正した場合

1. Mac 上の `M5PaperS3_NewsDashboard` で編集
2. commit / push
3. 再ビルドして M5PaperS3 へ書き込み
