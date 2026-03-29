# Operations

English: [operations.md](operations.md)

## 日常運用

### Raspberry Pi 側反映

```sh
cd ~/m5papers3
git pull
systemctl --user restart m5news-http.service
systemctl --user restart m5news-generate.timer
```

### M5 側反映

```sh
cd /Users/tomato/Documents/Arduino/M5PaperS3_NewsDashboard
arduino-cli compile -b m5stack:esp32:m5stack_papers3 .
```

その後、実機へ書き込みます。

## トラブル時の切り分け

### M5 がページ遷移しない

まず確認すること:

- Raspberry Pi 側 HTTP server が起動しているか
- `index.png` が取れるか
- `index.version` が取れるか

### Raspberry Pi 側 HTTP 確認

```sh
systemctl --user status m5news-http.service
ss -tulpn | grep 8010
curl -I http://127.0.0.1:8010/index.png
```

### PNG 自動生成確認

```sh
systemctl --user status m5news-generate.timer
journalctl --user -u m5news-generate.service -n 100 --no-pager
```

## README と docs の更新ルール

- README は入口にする
- 詳細仕様は `docs/` に置く
- 設計理由や制約を優先して書く
- 実装変更時は関連する docs だけ更新する
