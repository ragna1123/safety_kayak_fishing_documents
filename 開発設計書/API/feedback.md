## Feedback
### お問い合わせの送信
- POST `/api/feedbacks`
- 説明:ユーザーからのフィードバックを登録します。
- リクエストボディ:
```json
{
  "feedback":{
    "title":"お問い合わせ件名",
    "comment":"お問い合わせ内容"
  }
}
```
- ステータスコード: `201 Created`
- レスポンスボディ:
```json
{
  "message": "お問い合わせが送信されました"
}
```