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
</details>
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
