## Emergency contact
#### 緊急連絡先の登録
- POST `/api/emergency_contacts`
- 説明:新しい緊急連絡先を登録します。
- リクエストボディ:
```json
{
  "name": "山田太郎",
  "relationship": "友人",
  // "phone_number": "090-1234-5678",
  "email": "taro@example.com",
  // "line_id": "taro_line"
}
```
- ステータスコード: `201 Created`
- レスポンスボディ:
```json
{
  "contact_id": 1,
  "name": "山田太郎",
  "relationship": "友人",
  // "phone_number": "090-1234-5678",
  "email": "taro@example.com",
  // "line_id": "taro_line"
}
```

#### 緊急連絡先の一覧取得
- GET `/api/emergency_contacts`
- 説明:登録された緊急連絡先の一覧を取得します。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
"data": [
  {
    "contact_id": 1,
    "name": "山田太郎",
    "relationship": "友人",
    // "phone_number": "090-1234-5678",
    "email": "taro@example.com",
    // "line_id": "taro_line"
  },
  // 他の緊急連絡先...
]
```

#### 緊急連絡先の更新
- PUT `/api/emergency_contacts/{contact_id}`
- 説明:特定の緊急連絡先を更新します。
- リクエストボディ:
```json
{
  "name": "山田太郎",
  "relationship": "友人",
  // "phone_number": "090-1234-5678",
  "email": "taro@example.com",
  // "line_id": "taro_line"
}
```
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
{
  "contact_id": 1,
  "name": "山田太郎",
  "relationship": "友人",
  // "phone_number": "090-1234-5678",
  "email": "taro@example.com",
  // "line_id": "taro_line"
}
```

#### 緊急連絡先の削除
- DELETE `/api/emergency_contacts/{contact_id}`
- 説明:特定の緊急連絡先を削除します。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
{
  "massage":"緊急連絡先を削除しました。"
}
```