## Favorites

### お気に入り地点の登録
- POST `/api/favorites`
- 機能: ユーザーが指定した地点をお気に入りとして登録します。
- リクエストボディ:
```json
{
  "name":"地点の名称",
  "description":"地点の説明",
  "latitude":"緯度",
  "longitude":"経度"
}

```
- ステータスコード `201 Created`
- レスポンスボディ:
```json
{
  "favorite_id": "お気に入りの一意識別子",
  "user_id": "ユーザーの一意識別子",
  "location_data": {
    "location_id":"地点の一意識別子",
    "name":"地点の名称",
    "description":"地点の説明",
    "latitude":"緯度",
    "longitude":"経度"
  }
}
```



### お気に入り地点の一覧取得
- GET `/api/favorites`
- 特定のユーザーのお気に入り地点の一覧を取得します。
- ステータスコード `200 OK`
- レスポンスボディ:
```json
"data":[
  {
    "favorite_id": "お気に入りの一意識別子",
    "user_id": "ユーザーの一意識別子",
    "location_data": {
      "name":"地点の名称",
      "description":"地点の説明",
      "latitude":"緯度",
      "longitude":"経度"
    }
  },
  {...}
]
```

### お気に入り地点の削除
- DELETE `/api/favorites/{favorite_id}`
- 説明:特定のお気に入り地点を削除します。
- ステータスコード `200 OK`
- レスポンスボディ:
```json
{
  "message":"お気に入りを削除しました"
}
```