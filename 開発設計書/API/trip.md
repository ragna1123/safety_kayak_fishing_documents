# Trip

### 出船予定の登録
- メソッド: POST `/api/trips`
- 説明: 新しい出船予定を登録します。
- リクエストボディ:
```json
{
  "location_id": "地点ID",
  "departure_time": "出発時刻",
  "estimated_return_time": "予定帰投時刻",
  "details": "予定の詳細情報"
}
```
- ステータスコード: `201 Created`
- レスポンスボディ:
```json
{
  "message": "出船予定が登録されました"
}
```

### 出船予定の一覧取得
- メソッド: GET `/api/trips`
- 説明: 登録された出船予定の一覧を取得します。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
"data":[
  {
    "trip_id": "出船予定ID",
    "user_id": "ユーザーID",
    "location_id": "地点ID",
    "departure_time": "出発時刻",
    "estimated_return_time": "予定帰投時刻",
    "details": "詳細情報",
    "safety_score": "安全スコア"
  },
  {...}
]
```

### 出船予定の更新
- メソッド: PUT `/api/trips/{trip_id}`
- 説明: 特定の出船予定を更新します。
- リクエストボディ:
```json
{
  "location_id": "新しい地点ID",
  "departure_time": "新しい出発時刻",
  "estimated_return_time": "新しい予定帰投時刻",
  "purpose": "新しい出船目的",
  "details": "予定の詳細情報"
}
```
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
{
  "message": "出船予定が更新されました"
}
```

### 出船予定の削除
- DELETE `/api/trips/{trip_id}`
- 説明:特定の出船予定を削除します。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
{
  "message": "出船予定が削除されました"
}
```
---

## Trip Return (帰投情報)

### 帰投情報の記録
- メソッド: POST
- エンドポイント: `/api/trips/{trip_id}/return`
- 説明: ユーザーが無事帰投したことを記録します。帰投時刻やその他の詳細情報を含むことができます。
- リクエストボディ:
```json
{
  "return_time": "帰投時刻",
  // "status": "帰投状態",  ここをどうする？
  "return_details": "帰投に関する詳細情報"
}
```
- ステータスコード: `201 Created`
- レスポンスボディ:
```json
{
  "message": "帰投情報が記録されました"
}
```

---

## Trip history
### トリップ履歴一覧取得
- メソッド: GET `/api/trips/{user_id}/history`
- 説明: ユーザーのトリップ履歴の一覧を取得します。これにより、ユーザーは過去に行ったトリップの詳細情報を確認することができます。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
"data":[
  {
    "trip_id": "トリップID",
    "user_id": "ユーザーID",
    "location_id": "地点ID",
    "departure_time": "出発時刻",
    "return_time": "帰投時刻",
    "details": "予定の詳細情報"
  },
  {...}
]
```


### 特定のトリップ履歴と特定の天気データの取得
- メソッド: GET `/api/trips/{trip_id}/weather/{weather_data_id}`
- 説明: 特定のトリップに関連する特定の天気データを取得します。これは、トリップの詳細ページで特定の時点の天気情報を表示する場合などに利用できます。
- ステータスコード: `200 OK`
- レスポンスボディ:
```json
{
  "weather_data_id": "天気データID",
  "trip_id": "トリップID",
  "date": "日付",
  "temperature": "温度",
  "weather_condition": "天候状況",
  "wind_speed": "風速",
  "wind_direction": "風向き",
  "humidity": "湿度",
  "additional_info": "追加情報"
}
```

