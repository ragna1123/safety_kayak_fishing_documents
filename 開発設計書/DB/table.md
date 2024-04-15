# テーブル定義

## Users (ユーザー情報)

| Field               | Type          | Description         | Constraints          |
|---------------------|---------------|---------------------|----------------------|
| `user_id`           | INT           | ユーザーの一意識別子 | PK, AI, UQ           |
| `username`          | VARCHAR(255)  | ユーザー名          | NN                   |
| `email`             | VARCHAR(255)  | メールアドレス      | UQ, NN               |
| `password_hash`     | VARCHAR(255)  | パスワードのハッシュ値 | NN                |
| `profile_image_url` | VARCHAR(255)  | プロフィール画像のURL | NULL許容           |
| `line_id`           | VARCHAR(255)  | ラインのID          | NULL許容             |


---

## Locations (地点)

| Field          | Type          | Description       | Constraints          |
|----------------|---------------|-------------------|----------------------|
| `location_id`  | INT           | 地点の一意識別子   | PK, AI, UQ           |
| `latitude`     | DECIMAL(10, 8)| 緯度              | NN                   |
| `longitude`    | DECIMAL(11, 8)| 経度              | NN                   |


## FavoriteLocations (お気に入り地点)

| Field         | Type          | Description            | Constraints         |
|---------------|---------------|------------------------|---------------------|
| `favorite_id` | INT           | お気に入りの一意識別子  | PK, AI, UQ          |
| `user_id`     | INT           | ユーザーの一意識別子    | FK                  |
| `location_id` | INT           | 地点の一意識別子        | FK                  |
| `name`        | VARCHAR(255)  | 地点の名称             | NN                  |
| `description` | TEXT          | 地点の説明             | NULL許容            |


## Trips (出船スケジュール)

| Field                   | Type     | Description           | Constraints     |
|-------------------------|----------|-----------------------|-----------------|
| `trip_id`               | INT      | 出船予定の一意識別子   | PK, AI, UQ      |
| `user_id`               | INT      | ユーザーのID          | FK              |
| `location_id`           | INT      | 地点のID              | FK              |
| `departure_time`        | DATETIME | 出発時刻              | NN              |
| `estimated_return_time` | DATETIME | 予定帰投時刻          | NN              |
| `details`               | TEXT     | 予定の詳細情報        | NULL許容        |
| `safety_score`          | INT      | 安全スコア            | NULL許容        |
| `sunrise_time`          | DATETIME | 日の出時刻            | NULL許容        |
| `sunset_time`           | DATETIME | 日の入り時刻          | NULL許容        |
| `return_time`           | DATETIME | 帰投時刻              | NULL許容        |
| `return_details`        | TEXT     | 帰投に関する詳細情報  | NULL許容        |

---
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
## WeatherData(気象データ)
| Field                | Type           | Description                                       | Constraints            |
|----------------------|----------------|---------------------------------------------------|------------------------|
| `time`               | TIMESTAMP      | UTCのタイムスタンプ                               | NOT NULL               |
| `airTemperature`     | FLOAT          | 気温（摂氏）                                      |                        |
| `pressure`           | FLOAT          | 気圧 (hPa)                                        |                        |
| `cloudCover`         | INT            | 合計クラウド カバレッジ (パーセント)              | BETWEEN 0 AND 100      |
| `gust`               | FLOAT          | 突風（メートル/秒）                               |                        |
| `humidity`           | INT            | 相対湿度 (パーセント)                             | BETWEEN 0 AND 100      |
| `precipitation`      | FLOAT          | 平均降水量 (kg/m²/h) = mm/h                       |                        |
| `swellDirection`     | FLOAT          | うねり波の方向                                    | BETWEEN 0 AND 360      |
| `swellHeight`        | FLOAT          | うねりの波の高さ（メートル）                      |                        |
| `swellPeriod`        | FLOAT          | うねり波の周期（秒）                              |                        |
| `visibility`         | FLOAT          | 水平視程（km）                                    |                        |
| `waterTemperature`   | FLOAT          | 水温（摂氏）                                      |                        |
| `waveDirection`      | FLOAT          | 風とうねり波が合わさった方向                     | BETWEEN 0 AND 360      |
| `waveHeight`         | FLOAT          | 風とうねりを合わせたかなりの高さ（メートル単位） |                        |
| `wavePeriod`         | FLOAT          | 風とうねりを合わせた波の周期（秒）               |                        |
| `windWaveDirection`  | FLOAT          | 風波の方向                                        | BETWEEN 0 AND 360      |
| `windWaveHeight`     | FLOAT          | 風波の高さ (メートル)                             |                        |
| `windWavePeriod`     | FLOAT          | 風波の周期（秒）                                  |                        |
| `windDirection`      | FLOAT          | 海抜10mにおける風向き                             | BETWEEN 0 AND 360      |
| `windSpeed`          | FLOAT          | 海抜 10 メートルにおける風速 (メートル/秒)        |                        |


## TripWeather (トリップと気象予報の関連)

| Field            | Type          | Description              | Constraints         |
|------------------|---------------|--------------------------|---------------------|
| `trip_weather_id`| INT           | トリップと気象の関連ID   | PK, AI, UQ          |
| `trip_id`        | INT           | トリップの一意識別子     | FK                  |
| `weather_data_id`| INT           | 気象データの一意識別子   | FK                  |

---

## タイドデータ (TideData)

| Field         | Type         | Description           | Constraints    |
|---------------|--------------|-----------------------|----------------|
| `tide_id`     | INT          | タイドデータの一意識別子 | PK, AI, UQ    |
| `location_id` | INT          | 地点のID              | FK             |
| `time`        | DATETIME     | 潮の状態の時刻         | NN             |
| `type`        | VARCHAR(10)  | 潮の状態（満潮または干潮） | NN          |
| `height`      | FLOAT        | 潮の高さ (メートル)    | NN             |

## トリップとタイドデータの関連 (TripTide)

| Field         | Type         | Description              | Constraints    |
|---------------|--------------|--------------------------|----------------|
| `trip_tide_id`| INT          | トリップとタイドの関連ID | PK, AI, UQ     |
| `trip_id`     | INT          | トリップの一意識別子     | FK             |
| `tide_data_id`     | INT          | タイドデータの一意識別子  | FK             |

---

## Feedbacks (フィードバック)

| Field          | Type         | Description           | Constraints        |
|----------------|--------------|-----------------------|--------------------|
| `feedback_id`  | INT          | フィードバックの一意識別子 | PK, AI, UQ       |
| `title`        | TEXT         | お問い合わせ件名      | NN                |
| `comment`      | TEXT         | コメント              | NN                |
| `user_id`      | INT          | ユーザーのID          | FK                |



![alt text](ER.png)