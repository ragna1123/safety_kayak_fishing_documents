# API

## User

#### ユーザー登録
- POST `/api/users`
  - ユーザー名、メールアドレス、パスワードを受け取り、新しいユーザーを登録します。

#### ユーザーログイン
- POST `/api/users/login`
  - メールアドレスとパスワードを受け取り、認証トークンを返します。

#### ユーザー情報取得
- GET `/api/users/{user_id}`
  - ユーザーIDに基づいてユーザー情報を取得します。

#### ユーザー情報更新
- PUT `/api/users/{user_id}`
  - ユーザー名やプロフィール画像など、ユーザー情報を更新します。
---
## Location
#### 地点の登録
- POST `/api/locations`
  - 新しい地点を登録します。

#### 地点の一覧取得
- GET `/api/locations`
  - 登録された地点の一覧を取得します。

#### 地点情報の更新
- PUT `/api/locations/{location_id}`
  - 特定の地点情報を更新します。

#### 地点情報の削除
- DELETE `/api/locations/{location_id}`
  - 特定の地点を削除します。
---
## Trip
#### 出船予定の登録
- POST `/api/trips`
  - 新しい出船予定を登録します。

#### 出船予定の一覧取得
- GET `/api/trips`
  - 登録された出船予定の一覧を取得します。

#### 出船予定の更新
- PUT `/api/trips/{trip_id}`
  - 特定の出船予定を更新します。

#### 出船予定の削除
- DELETE `/api/trips/{trip_id}`
  - 特定の出船予定を削除します。
---
## Trip Return (帰投情報)

#### 帰投情報の記録
- POST `/api/trips/{trip_id}/return`
  - ユーザーが無事帰投したことを記録します。帰投時刻やその他の詳細情報を含むことができます。

#### 帰投情報の確認
- GET `/api/trips/{trip_id}/return`
  - 特定のトリップの帰投情報を取得します。ユーザーが予定通りに帰投したかどうかの確認に使用します。

#### 帰投情報の更新
- PUT `/api/trips/{trip_id}/return`
  - すでに記録された帰投情報を更新します。例えば、帰投時間の変更や、追加の詳細情報を記録する場合に使用します。

#### 帰投情報の削除
- DELETE `/api/trips/{trip_id}/return`
  - 誤って入力された帰投情報を削除します。

---
## Trip history
#### 特定のトリップに関連する天気データの一覧取得
- **GET** `/api/trips/{trip_id}/weather`
  - 特定のトリップに関連する天気データの一覧を取得します。これにより、ユーザーは過去の出船時の天気状況を履歴として閲覧することができます。

#### 特定のトリップと特定の天気データの取得
- **GET** `/api/trips/{trip_id}/weather/{weather_data_id}`
  - 特定のトリップに関連する特定の天気データを取得します。これは、トリップの詳細ページで特定の時点の天気情報を表示する場合などに利用できます。

---
## Emergency contact
#### 緊急連絡先の登録
- POST `/api/emergency_contacts`
  - 新しい緊急連絡先を登録します。

#### 緊急連絡先の一覧取得
- GET `/api/emergency_contacts`
  - 登録された緊急連絡先の一覧を取得します。

#### 緊急連絡先の更新
- PUT `/api/emergency_contacts/{contact_id}`
  - 特定の緊急連絡先を更新します。

#### 緊急連絡先の削除
- DELETE `/api/emergency_contacts/{contact_id}`
  - 特定の緊急連絡先を削除します。
---
## Feedback
#### フィードバックの送信
- POST `/api/feedbacks`
  - ユーザーからのフィードバックを登録します。
