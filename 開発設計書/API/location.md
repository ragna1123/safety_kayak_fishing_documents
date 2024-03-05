## Location
### 地点の登録
- POST `/api/locations`
- 説明:新しい地点を登録します。
- リクエストボディ:
```json
{
  "name": "北湖のポイント",
  "description": "深い水域に近い、カヤックフィッシングに最適な場所。",
  "latitude": 35.681236,
  "longitude": 139.767125
}
```
- ステータスコード: `201 Created`
- レスポンスボディ:
```json

{
  "location_id": 42,
  "name": "北湖のポイント",
  "description": "深い水域に近い、カヤックフィッシングに最適な場所。",
  "latitude": 35.681236,
  "longitude": 139.767125
}
```

<!-- ### 地点の一覧取得
- GET `/api/locations`
- 機能: ユーザーが登録したすべての地点の一覧を取得します。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
"data": [
  {
    "location_id": 1,
    "name": "北湖のポイント",
    "description": "深い水域に近い、カヤックフィッシングに最適な場所。",
    "latitude": 35.681236,
    "longitude": 139.767125
  },
  {
    "location_id": 2,
    "name": "南湖のエリア",
    "description": "小さな島の周りで魚が豊富なエリア。",
    "latitude": 35.658987,
    "longitude": 139.745438
  }
  // 他の地点...
]
``` -->

### 地点の取得
- GET `/api/locations/{location_id}`
- 説明:登録された地点の一覧を取得します。
  - ステータスコード: `200 OK`
- リクエストボディ:
```json
{
  "location_id": 1,
  "name": "北湖のポイント",
  "description": "深い水域に近い、カヤックフィッシングに最適な場所。",
  "latitude": 35.681236,
  "longitude": 139.767125
}
```


<!-- #### 地点情報の更新
- PUT `/api/locations/{location_id}`
  - 特定の地点情報を更新します。

#### 地点情報の削除
- DELETE `/api/locations/{location_id}`
  - 特定の地点を削除します。 -->