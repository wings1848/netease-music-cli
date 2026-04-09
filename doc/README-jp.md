# 网易云音楽 Agent Skills

`ncm-cli` に基づいた网易云音楽 AI Agent スキルパッケージ。

[オリジナル公式スキル](http://github.com/NetEase/skills) からユーザープライバシー情報収集に関するプロンプトインジェクションを削除し、大幅に精简してトークンを節約。

## 事前要件

ncm-cli のすべてのコマンド呼び出しは API Key に依存します。[网易云音楽オープンプラットフォーム](https://developer.music.163.com/st/developer/apply/account?type=INDIVIDUAL) で登録と申請を完了してください。[登録ガイド](https://developer.music.163.com/st/developer/document?docId=9504d35aa41a47c6ac9830b2dbf48f94)

## スキル概要

| スキル | 説明 | トリガーシナリオ |
|-------|------|----------------|
| netease-music-cli | ncm-cli で网易云音楽操作を実行 | 音楽再生、曲検索、再生制御、再生キュー管理、再生状態表示、再生リスト再生 |
| netease-music-assistant | 网易云音楽インテリジェントアシスタント、コア機能：嗜好分析、レコメンデーション、スケジュール配信 | 曲再生、プレイリスト/音楽推薦、スケジュール配信、音乐嗜好分析 |

---

## netease-music-cli

**ncm-cli で网易云音楽操作を実行。**

コア機能：

- ncm-cli ツールのインストールと設定
- 曲/プレイリスト/アルバム検索
- プレイリスト管理（作成、曲追加、表示）
- デイリーレコメンデーション取得
- ユーザー情報表示

### 環境要件：Node.js >= 18

- インストール方法：`npm install -g @music163/ncm-cli`
- インストール後 `ncm-cli configure` で設定完了、`ncm-cli login` でログイン認証完了

### コマンド早見表

```bash
# 現在のコマンドツリーを取得
ncm-cli commands

# ヘルプを取得
ncm-cli help <command>
```

---

## netease-music-assistant

**网易云音楽インテリジェントアシスタント。**

コア機能：

- 嗜好分析：ユーザーのいいね曲プレイリストの嗜好プロファイルを分析（24時間キャッシュ）
- レコメンデーション：プレイリスト/アルバム/シングル曲推薦、重複排除対応
- スケジュール配信：毎日のスケジュールタスクによる音楽配信をサポート

### 状態ファイル

| ファイル | 用途 |
|----------|------|
| `~/.config/ncm/ncm-preference.json` | ユーザー嗜好プロファイル |
| `~/.config/ncm/ncm-history.json` | 推薦履歴（重複排除） |
| `~/.config/ncm/ncm-schedule.json` | スケジュール配信設定 |