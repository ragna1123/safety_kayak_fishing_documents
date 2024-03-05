# Weather
### ロケーションベースの気象予報取得
- GET `/api/weather/forecast/{location_id}`
- 機能: 指定された地点の現在および将来の気象予報データを提供します。
- レスポンス (成功時):
- ステータスコード 200 OK
- レスポンスボディ:
```json
{
  "forecast_time": "2023-01-01T10:00:00Z",
  "temperature": 20,
  "wind_speed": 5,
  "wind_direction": "北東",
  "wave_height": 2,
  "weather_condition": "晴れ",
  "tide": "中潮",
  "tide_level": 1.5
}
```