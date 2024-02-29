# テーブル定義

## Users (ユーザー情報)

| Field             | Type         | Description         | Constraints          |
|-------------------|--------------|---------------------|----------------------|
| `user_id`         | INT          | ユーザーの一意識別子 | PK, AI, UQ           |
| `username`        | VARCHAR(255) | ユーザー名           | NN                   |
| `email`           | VARCHAR(255) | メールアドレス       | UQ, NN               |
| `password_hash`   | VARCHAR(255) | パスワードのハッシュ値 | NN                 |
| `profile_image_url` | VARCHAR(255) | プロフィール画像のURL | NULL許容           |

## Locations (釣行ポイント)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `location_id`    | INT           | 地点の一意識別子   | PK, AI, UQ           |
| `name`           | VARCHAR(255)  | 地点の名称         | NN                   |
| `description`    | TEXT          | 地点の説明         | NULL許容            |
| `latitude`       | DECIMAL(10, 8)| 緯度               | NN                   |
| `longitude`      | DECIMAL(11, 8)| 経度               | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |

## Trips (出船スケジュール)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `trip_id`        | INT           | 出船予定の一意識別子 | PK, AI, UQ          |
| `date_time`      | DATETIME      | 出船の日付と時間   | NN                   |
| `details`        | TEXT          | 予定の詳細情報     | NULL許容            |
| `safety_score`   | INT           | 安全スコア         | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |
| `location_id`    | INT           | 地点のID           | FK                   |

## EmergencyContacts (緊急連絡先情報)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `contact_id`     | INT           | 緊急連絡先の一意識別子 | PK, AI, UQ         |
| `name`           | VARCHAR(255)  | 緊急連絡先の名前   | NN                   |
| `relationship`   | VARCHAR(255)  | 関係               | NN                   |
| `phone_number`   | VARCHAR(20)   | 電話番号           | NULL許容            |
| `email`          | VARCHAR(255)  | メールアドレス     | NULL許容, UQ        |
| `line_id`        | VARCHAR(255)  | ラインのID         | NULL許容, 検討中    |
| `user_id`        | INT           | ユーザーのID       | FK                   |

## WeatherData (釣行気象履歴)

| Field              | Type          | Description             | Constraints            |
|--------------------|---------------|-------------------------|------------------------|
| `weather_data_id`  | INT           | 天気データの一意識別子   | PK, AI, UQ             |
| `location_id`      | INT           | 地点の一意識別子         | FK                     |
| `trip_id`          | INT           | 出船予定の一意識別子     | FK, NULL許容           |
| `timestamp`        | DATETIME      | 観測日時                 | NN                     |
| `temperature`      | FLOAT         | 気温（°C）              |                        |
| `wind_speed`       | FLOAT         | 風速（m/s）             |                        |
| `wind_direction`   | VARCHAR(255)  | 風向                   |                        |
| `wave_height`      | FLOAT         | 波の高さ（m）           |                        |
| `weather_condition`| VARCHAR(255)  | 天気の状態              |                        |
| `tide`             | VARCHAR(255)  | 潮の状態                |                        |
| `tide_level`       | FLOAT         | 潮位（m）               | NULL許容               |


## Feedbacks (フィードバック)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `feedback_id`    | INT           | フィードバックの一意識別子 | PK, AI, UQ       |
| `comment`        | TEXT          | コメント           | NN                   |


| `user_id`        | INT           | ユーザーのID       | FK                   |

![alt text](ER.png)