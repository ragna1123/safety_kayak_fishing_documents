## Users

| Field             | Type         | Description         | Constraints          |
|-------------------|--------------|---------------------|----------------------|
| `user_id`         | INT          | ユーザーの一意識別子 | PK, AI, UQ           |
| `username`        | VARCHAR(255) | ユーザー名           | NN                   |
| `email`           | VARCHAR(255) | メールアドレス       | UQ, NN               |
| `password_hash`   | VARCHAR(255) | パスワードのハッシュ値 | NN                 |
| `profile_image_url` | VARCHAR(255) | プロフィール画像のURL | NULL許容           |

## Locations

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `location_id`    | INT           | 地点の一意識別子   | PK, AI, UQ           |
| `name`           | VARCHAR(255)  | 地点の名称         | NN                   |
| `description`    | TEXT          | 地点の説明         | NULL許容            |
| `latitude`       | DECIMAL(10, 8)| 緯度               | NN                   |
| `longitude`      | DECIMAL(11, 8)| 経度               | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |

## Trips

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `trip_id`        | INT           | 出船予定の一意識別子 | PK, AI, UQ          |
| `date_time`      | DATETIME      | 出船の日付と時間   | NN                   |
| `details`        | TEXT          | 予定の詳細情報     | NULL許容            |
| `safety_score`   | INT           | 安全スコア         | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |
| `location_id`    | INT           | 地点のID           | FK                   |

## EmergencyContacts

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `contact_id`     | INT           | 緊急連絡先の一意識別子 | PK, AI, UQ         |
| `name`           | VARCHAR(255)  | 緊急連絡先の名前   | NN                   |
| `relationship`   | VARCHAR(255)  | 関係               | NN                   |
| `phone_number`   | VARCHAR(20)   | 電話番号           | NULL許容            |
| `email`          | VARCHAR(255)  | メールアドレス     | NULL許容, UQ        |
| `line_id`        | VARCHAR(255)  | ラインのID         | NULL許容, 検討中    |
| `user_id`        | INT           | ユーザーのID       | FK                   |

## Feedbacks

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `feedback_id`    | INT           | フィードバックの一意識別子 | PK, AI, UQ       |
| `comment`        | TEXT          | コメント           | NN                   |
| `created_at`     | DATETIME      | 作成日時           | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |

