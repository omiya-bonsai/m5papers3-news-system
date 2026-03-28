# Repositories

## 3 本構成

このシステムは次の 3 本のリポジトリで運用します。

### m5papers3-news-system

役割:

- 統合ハブ
- 全体構成説明
- 導入順
- 運用フロー

## M5PaperS3_NewsDashboard

役割:

- M5PaperS3 側スケッチ
- `docs/` に設計メモを保持
- キャッシュ / UI / 既読表示 / 電源ポリシーを担当

ローカル例:

```text
/Users/tomato/Documents/Arduino/M5PaperS3_NewsDashboard
```

## m5papers3-news-server

役割:

- Raspberry Pi 側スクリプト
- PNG 生成
- `index.version` 生成
- `systemd/` と HTTP 配信

ローカル例:

```text
/Users/tomato/Documents/projects/m5papers3-news-server
```

## 役割分離の考え方

### 統合ハブに置くもの

- 全体像
- セットアップ導線
- リポジトリ間の関係

### M5 側に置くもの

- デバイス固有の実装
- 表示仕様
- タッチ / スワイプ
- キャッシュと電源制御

### Raspberry Pi 側に置くもの

- 生成・配信ロジック
- systemd 運用
- フォント要件

## 公開時の考え方

- 実 NHK コンテンツ画像は公開しない
- 生成済み PNG は repo に含めない
- コード、設定例、README、docs を公開対象にする
