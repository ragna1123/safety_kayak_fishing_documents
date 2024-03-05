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