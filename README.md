# Spotify Playlist Sorter

このプロジェクトは、Spotify プレイリストを **リリース日順** に自動で並べ替える Python スクリプトです。
ユーザー自身の Spotify アカウントを使って操作するため、**Authorization Code Flow** を利用しています。

---

## 使い方

### 1. 必要条件

* Python 3.x
* 以下の Python ライブラリ

  ```bash
  pip install flask requests python-dotenv
  ```
* Spotify Developer アカウント
* Spotify アプリ作成済み（Client ID と Client Secret を取得）
* Redirect URI に `http://localhost:8888/callback` を登録

---

### 2. プロジェクト構成

```
spotify_sort/
├─ spotify.py       # メインスクリプト
└─ .env             # 秘密情報 (Client ID / Secret)
```

#### `.env` の内容例

```text
SPOTIFY_CLIENT_ID=あなたのClientID
SPOTIFY_CLIENT_SECRET=あなたのClientSecret
```

※ `.env` は絶対に GitHub などに公開しないこと

---

### 3. 実行方法

1. ターミナルでスクリプトを実行

```bash
python spotify.py
```

2. 表示される URL (`http://localhost:8888/`) をブラウザで開く
3. Spotify にログインし、アプリのアクセス許可を承認
4. 認証後、自動的にプレイリストが **リリース日順** に並べ替えられる

* ブラウザは並べ替え中に閉じても問題ありません
* 曲数が多い場合（例: 500曲以上）は数秒〜数十秒かかります

---

### 4. 注意事項

* 本スクリプトはローカル環境向けです。公開サーバーでの運用は推奨しません
* `.env` に秘密情報を保存し、GitHub にはアップロードしないでください
* Spotify API の仕様変更により動作しなくなる可能性があります

---

### 5. カスタマイズ

* プレイリスト ID を変更したい場合、`spotify.py` の `PLAYLIST_ID` を編集してください
* 並べ替えの基準を変更する場合、`sort_playlist_by_release_date()` 内の `key` を変更可能です

---

✅ これで、Spotify プレイリストのリリース日順並べ替えが簡単に行えます
