## Favorites

#### お気に入り地点の登録
- POST `/api/favorites`
  - ユーザーIDと地点IDを受け取り、新しいお気に入り地点を登録します。

#### お気に入り地点の一覧取得
- GET `/api/favorites/{user_id}`
  - 特定のユーザーのお気に入り地点の一覧を取得します。

#### お気に入り地点の削除
- DELETE `/api/favorites/{favorite_id}`
  - 特定のお気に入り地点を削除します。
