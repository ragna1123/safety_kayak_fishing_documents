# テーブル定義

## Users (ユーザー情報)

| Field             | Type         | Description         | Constraints          |
|-------------------|--------------|---------------------|----------------------|
| `user_id`         | INT          | ユーザーの一意識別子 | PK, AI, UQ           |
| `username`        | VARCHAR(255) | ユーザー名           | NN                   |
| `email`           | VARCHAR(255) | メールアドレス       | UQ, NN               |
| `password_hash`   | VARCHAR(255) | パスワードのハッシュ値 | NN                 |
| `profile_image_url` | VARCHAR(255) | プロフィール画像のURL | NULL許容           |

---

## Locations (地点)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `location_id`    | INT           | 地点の一意識別子   | PK, AI, UQ           |
| `latitude`       | DECIMAL(10, 8)| 緯度               | NN                   |
| `longitude`      | DECIMAL(11, 8)| 経度               | NN                   |

## FavoriteLocations (お気に入り地点)

| Field          | Type        | Description            | Constraints            |
|----------------|-------------|------------------------|------------------------|
| `favorite_id`  | INT         | お気に入りの一意識別子  | PK, AI, UQ             |
| `user_id`      | INT         | ユーザーの一意識別子    | FK                     |
| `location_id`  | INT         | 地点の一意識別子        | FK                     |
| `name`           | VARCHAR(255)  | 地点の名称         | NN                   |
| `description`    | TEXT          | 地点の説明         | NULL許容            |

## Trips (出船スケジュール)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `trip_id`        | INT           | 出船予定の一意識別子 | PK, AI, UQ          |
| `user_id`        | INT           | ユーザーのID       | FK                   |
| `location_id`    | INT           | 地点のID           | FK                   |
| `departure_time`      | DATETIME | 出発時刻           | NN                   |
| `estimated_return_time` | DATETIME | 予定帰投時刻      | NN                   |
| `details`        | TEXT          | 予定の詳細情報      | NULL許容            |
| `safety_score`   | INT           | 安全スコア         | NULL許容            |
| `sunrise_time`       | DATETIME         | 日の出時刻               | NULL許容               |
| `sunset_time`       | DATETIME         | 日の入り時刻               | NULL許容               |
| `return_time`    | DATETIME    | 帰投時刻                   | NULL許容                    |
| `return_details` | TEXT        | 帰投に関する詳細情報       | NULL許容               |

## EmergencyContacts (緊急連絡先情報)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `contact_id`     | INT           | 緊急連絡先の一意識別子 | PK, AI, UQ         |
| `user_id`        | INT           | ユーザーのID       | FK                   |
| `name`           | VARCHAR(255)  | 緊急連絡先の名前   | NN                   |
| `relationship`   | VARCHAR(255)  | 関係               | NN                   |
| `phone_number`   | VARCHAR(20)   | 電話番号           | NULL許容            |
| `email`          | VARCHAR(255)  | メールアドレス     | NN, UQ        |
| `line_id`        | VARCHAR(255)  | ラインのID         | NULL許容, 検討中    |

---

## WeatherData (気象データ)

| Field              | Type          | Description             | Constraints            |
|--------------------|---------------|-------------------------|------------------------|
| `weather_data_id`  | INT           | 天気データの一意識別子   | PK, AI, UQ             |
| `weather_condition`| VARCHAR(255)  | 天気の状態              | NN                    |
| `timestamp`        | DATETIME      | 観測日時                 | NN                     |
| `temperature`      | FLOAT         | 気温（°C）              | NN                      |
| `wind_speed`       | FLOAT         | 風速（m/s）             | NN                     |
| `wind_direction`   | VARCHAR(255)  | 風向                   | NN                     |
| `wave_height`      | FLOAT         | 波の高さ（m）           | NN                     |
| `tide`             | VARCHAR(255)  | 潮の状態                | NULL許容               |
| `tide_level`       | FLOAT         | 潮位（m）               | NULL許容               |

## TripWeather (トリップと気象予報の関連)

| Field                | Type          | Description                     | Constraints            |
|----------------------|---------------|---------------------------------|------------------------|
| `trip_weather_id`   | INT           | トリップと気象の関連ID      | PK, AI, UQ             |
| `trip_id`            | INT           | トリップの一意識別子            | FK                     |
| `weather_data_id`   | INT           | 気象データの一意識別子      | FK                     |

---

## Feedbacks (フィードバック)

| Field            | Type          | Description       | Constraints          |
|------------------|---------------|-------------------|----------------------|
| `feedback_id`    | INT           | フィードバックの一意識別子 | PK, AI, UQ       |
| `title`          | TEXT          | お問い合わせ件名         | NN               |
| `comment`        | TEXT          | コメント           | NN                   |
| `user_id`        | INT           | ユーザーのID       | FK                   |


![alt text](ER.png)ge