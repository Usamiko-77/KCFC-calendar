# KCFC Team Calendar

Firebase Realtime Databaseを使った、ログイン不要のチーム予定共有Webアプリです。

## 主な機能
- 月表示・今後の予定一覧
- リアルタイム共有
- 予定の追加・編集・削除
- 出席確認（参加・未定・不参加）
- コメント
- 写真・PDF添付（Firebase Storage使用）
- 検索、ICS書き出し、ダークモード
- ブラウザ通知（サイトを開いている間のみ）

## Realtime Database ルール
Firebase Console → Realtime Database → ルールに以下を設定して公開してください。

```json
{
  "rules": {
    "events": {
      ".read": true,
      ".write": true
    }
  }
}
```

## 添付ファイルを使う場合
Firebase Consoleで Storage を有効化し、Storageのルールを設定する必要があります。
ログインなし運用の簡易例：

```txt
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /attachments/{allPaths=**} {
      allow read, write: if true;
    }
  }
}
```

注意：上記はURLを知る人が書き込める設定です。チーム内限定でURLを共有してください。

## GitHub Pages公開
`index.html`、`style.css`、`app.js` をリポジトリ直下へ置き、Settings → Pages → Deploy from a branch → main / root を選択します。
