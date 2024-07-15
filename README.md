# safety_kayak_fishing

## オリジナルプロダクトの URL

[セーフティカヤックフィッシングアプリ](https://safety-kayak.com)

## 概要

> カヤックフィッシングの事故率上昇に対処し、禁止になることを防ぐため、「海にも登山届のような出船届を！」

```bash
「海上での、万が一に備える」 をしたい
「SUP,カヤックフィッシングをする方」 向けの
「プロダクト名:セーフティカヤックフィッシング」 は
「SUP,カヤックフッシング用のサポートアプリ」 です。

これは 「帰還設定時刻を設定する」 ことができ、
「windyの風予報やタイドグラフアプリなど」 とは違って、
「予報だけでなく、設定時間に帰還できなかった際に身内にメールが飛ぶ機能」
がある。

```

## 工夫した点

- 直感的にわかるようにマップ上でクリックした位置情報から、海の状況を取得できるようにしました。
- バックエンドではテスト駆動開発を行い、安全に開発を進めました。
- GitHubActions を使用して Git へのプッシュをトリガーにテストとデプロイが行えるように CI/CD を組みました。
- 開発段階のため、コスト削減を重視して EC2 の無料枠を積極的に採用しています。

## GitHub リポジトリ

### ドキュメント

[https://github.com/ragna1123/safety_kayak_fishing_documents]

### フロントエンドリポジトリ

[https://github.com/ragna1123/safety-kayak-fishing-frontend]

### バックエンドリポジトリ

[https://github.com/ragna1123/safety-kayak-fishing-backend]

## 画面キャプチャ

### ログイン画面

![alt text](開発設計書/kayak%20SS/ログイン.png)

### ホーム

![alt text](開発設計書/kayak%20SS/ホーム.png)

### マップピンの週間天気と詳細

![alt text](開発設計書/kayak%20SS/地点詳細.png)

### 出船予定登録画面

![alt text](開発設計書/kayak%20SS/出船予定登録.png)

### 出船予定日の天気詳細

![alt text](開発設計書/kayak%20SS/出船予定詳細天気.png)

### 　緊急連絡先登録

![alt text](開発設計書/kayak%20SS/緊急連絡先登録.png)

## 使用技術

<details>
<summary>使用技術一覧</summary>

## フロントエンド

### フレームワーク

- Next.js

### ライブラリ

#### 型定義

- TypeScript

#### 状態管理

- Recoil

#### フェッチング、キャッシュ関係

- Axios
- ~~RWS~~

#### CSS,UI 関係

- TailwindCSS
- Daisy UI
- Hero Icons

### テスト関係

- ~~Jest~~

## バックエンド

### フレームワーク

- Ruby on Rails(API モード)

### ライブラリ

- ~~ActionMailer(メール送信)~~
- JWT(認証)
- sidekiq
  (時刻で処理を起動させる非同期処理ライブラリ※今回はメール送信,LINE アラート機能に使用)

#### テスト

- Rspec
- factoryBot

## データベース

#### RDB

- Postglesql

#### NoSQL

- Redis(sidekiq に使用)

## 外部 API

### 地図

- GoogleMap(地図) https://developers.google.com/maps?hl=ja

### 天気予報,潮位関係

- StormGlassIO(海況情報、天気を提供する API)
- Visualcrossing(週間天気予報を提供する APU)
- SunriseSunsetAPI(日の出、日の入りを手供する API)
</details>

## ER 図

![alt text](開発設計書/DB/ER.png)

<details>
<summary>テーブル一覧</summary>

### Users (ユーザー情報)

| Field               | Type         | Description            | Constraints |
| ------------------- | ------------ | ---------------------- | ----------- |
| `user_id`           | INT          | ユーザーの一意識別子   | PK, AI, UQ  |
| `username`          | VARCHAR(255) | ユーザー名             | NN          |
| `email`             | VARCHAR(255) | メールアドレス         | UQ, NN      |
| `password_hash`     | VARCHAR(255) | パスワードのハッシュ値 | NN          |
| `profile_image_url` | VARCHAR(255) | プロフィール画像の URL | NULL 許容   |
| `line_id`           | VARCHAR(255) | ラインの ID            | NULL 許容   |

---

### Locations (地点)

| Field         | Type           | Description      | Constraints |
| ------------- | -------------- | ---------------- | ----------- |
| `location_id` | INT            | 地点の一意識別子 | PK, AI, UQ  |
| `latitude`    | DECIMAL(10, 8) | 緯度             | NN          |
| `longitude`   | DECIMAL(11, 8) | 経度             | NN          |

### FavoriteLocations (お気に入り地点)

| Field         | Type         | Description            | Constraints |
| ------------- | ------------ | ---------------------- | ----------- |
| `favorite_id` | INT          | お気に入りの一意識別子 | PK, AI, UQ  |
| `user_id`     | INT          | ユーザーの一意識別子   | FK          |
| `location_id` | INT          | 地点の一意識別子       | FK          |
| `name`        | VARCHAR(255) | 地点の名称             | NN          |
| `description` | TEXT         | 地点の説明             | NULL 許容   |

### Trips (出船スケジュール)

| Field                   | Type     | Description          | Constraints |
| ----------------------- | -------- | -------------------- | ----------- |
| `trip_id`               | INT      | 出船予定の一意識別子 | PK, AI, UQ  |
| `user_id`               | INT      | ユーザーの ID        | FK          |
| `location_id`           | INT      | 地点の ID            | FK          |
| `departure_time`        | DATETIME | 出発時刻             | NN          |
| `estimated_return_time` | DATETIME | 予定帰投時刻         | NN          |
| `details`               | TEXT     | 予定の詳細情報       | NULL 許容   |
| `safety_score`          | INT      | 安全スコア           | NULL 許容   |
| `sunrise_time`          | DATETIME | 日の出時刻           | NULL 許容   |
| `sunset_time`           | DATETIME | 日の入り時刻         | NULL 許容   |
| `return_time`           | DATETIME | 帰投時刻             | NULL 許容   |
| `return_details`        | TEXT     | 帰投に関する詳細情報 | NULL 許容   |

---

### EmergencyContacts (緊急連絡先情報)

| Field          | Type         | Description            | Constraints       |
| -------------- | ------------ | ---------------------- | ----------------- |
| `contact_id`   | INT          | 緊急連絡先の一意識別子 | PK, AI, UQ        |
| `user_id`      | INT          | ユーザーの ID          | FK                |
| `name`         | VARCHAR(255) | 緊急連絡先の名前       | NN                |
| `relationship` | VARCHAR(255) | 関係                   | NN                |
| `phone_number` | VARCHAR(20)  | 電話番号               | NULL 許容         |
| `email`        | VARCHAR(255) | メールアドレス         | NN, UQ            |
| `line_id`      | VARCHAR(255) | ラインの ID            | NULL 許容, 検討中 |

---

### WeatherData(気象データ)

| Field               | Type      | Description                                      | Constraints       |
| ------------------- | --------- | ------------------------------------------------ | ----------------- |
| `time`              | TIMESTAMP | UTC のタイムスタンプ                             | NOT NULL          |
| `airTemperature`    | FLOAT     | 気温（摂氏）                                     |                   |
| `pressure`          | FLOAT     | 気圧 (hPa)                                       |                   |
| `cloudCover`        | INT       | 合計クラウド カバレッジ (パーセント)             | BETWEEN 0 AND 100 |
| `gust`              | FLOAT     | 突風（メートル/秒）                              |                   |
| `humidity`          | INT       | 相対湿度 (パーセント)                            | BETWEEN 0 AND 100 |
| `precipitation`     | FLOAT     | 平均降水量 (kg/m²/h) = mm/h                      |                   |
| `swellDirection`    | FLOAT     | うねり波の方向                                   | BETWEEN 0 AND 360 |
| `swellHeight`       | FLOAT     | うねりの波の高さ（メートル）                     |                   |
| `swellPeriod`       | FLOAT     | うねり波の周期（秒）                             |                   |
| `visibility`        | FLOAT     | 水平視程（km）                                   |                   |
| `waterTemperature`  | FLOAT     | 水温（摂氏）                                     |                   |
| `waveDirection`     | FLOAT     | 風とうねり波が合わさった方向                     | BETWEEN 0 AND 360 |
| `waveHeight`        | FLOAT     | 風とうねりを合わせたかなりの高さ（メートル単位） |                   |
| `wavePeriod`        | FLOAT     | 風とうねりを合わせた波の周期（秒）               |                   |
| `windWaveDirection` | FLOAT     | 風波の方向                                       | BETWEEN 0 AND 360 |
| `windWaveHeight`    | FLOAT     | 風波の高さ (メートル)                            |                   |
| `windWavePeriod`    | FLOAT     | 風波の周期（秒）                                 |                   |
| `windDirection`     | FLOAT     | 海抜 10m における風向き                          | BETWEEN 0 AND 360 |
| `windSpeed`         | FLOAT     | 海抜 10 メートルにおける風速 (メートル/秒)       |                   |

### TripWeather (トリップと気象予報の関連)

| Field             | Type | Description             | Constraints |
| ----------------- | ---- | ----------------------- | ----------- |
| `trip_weather_id` | INT  | トリップと気象の関連 ID | PK, AI, UQ  |
| `trip_id`         | INT  | トリップの一意識別子    | FK          |
| `weather_data_id` | INT  | 気象データの一意識別子  | FK          |

---

### タイドデータ (TideData)

| Field         | Type        | Description                | Constraints |
| ------------- | ----------- | -------------------------- | ----------- |
| `tide_id`     | INT         | タイドデータの一意識別子   | PK, AI, UQ  |
| `location_id` | INT         | 地点の ID                  | FK          |
| `time`        | DATETIME    | 潮の状態の時刻             | NN          |
| `type`        | VARCHAR(10) | 潮の状態（満潮または干潮） | NN          |
| `height`      | FLOAT       | 潮の高さ (メートル)        | NN          |

### トリップとタイドデータの関連 (TripTide)

| Field          | Type | Description               | Constraints |
| -------------- | ---- | ------------------------- | ----------- |
| `trip_tide_id` | INT  | トリップとタイドの関連 ID | PK, AI, UQ  |
| `trip_id`      | INT  | トリップの一意識別子      | FK          |
| `tide_data_id` | INT  | タイドデータの一意識別子  | FK          |

---

### Feedbacks (フィードバック)

| Field         | Type | Description                | Constraints |
| ------------- | ---- | -------------------------- | ----------- |
| `feedback_id` | INT  | フィードバックの一意識別子 | PK, AI, UQ  |
| `title`       | TEXT | お問い合わせ件名           | NN          |
| `comment`     | TEXT | コメント                   | NN          |
| `user_id`     | INT  | ユーザーの ID              | FK          |

</details>

## インフラ構成図

![alt text](開発設計書/ENV/infrastructure/infrastructure.png)

## 機能一覧(非実装機能は打ち消し線で表示)

### 1. ユーザー管理

- ユーザー登録・ログイン機能。
- プロフィール情報の登録・編集。

### 2. マップと地点管理

- マップ上に出船地点のピンを打つ機能。
- ~~ユーザー個別のマイポイント（秘密の釣り場）の登録・管理。~~
- 地点ごとの詳細情報閲覧（潮位、天気、風、波など）。

### 3. 天気予報と海上情報

- 各地点での天気予報情報の取得と表示。
- 風速、風向きの情報表示。
- 波の高さと周期の情報表示。
- 潮位情報の表示。

### 4. 出船予報と計画管理

- 出船予定の作成、編集、削除機能。
- ~~出船に適した条件を基にした安全スコアの算出。~~
- ~~危険な条件下での出船時に警告を発する機能。~~
- 予定された出船と帰還時間の管理。

### 5. 出船中の監視

- ~~出船中に危険度が上がった場合に知らせる機能~~
- ~~出船中に定期的に海況を知らせる機能~~

### 6. 出船履歴から気象データを提供

- ~~過去の出船した気象データの提供。~~
- ~~当時状況から自身の出船判断へ役立てる機能。~~

### 7. 安全意識向上と啓発

- ~~安全航行に関する情報の提供。~~
- ~~海上での事故防止に役立つ情報の発信。~~
- ~~事故発生時の対処法や連絡先情報の提供。~~

### 8. 緊急連絡機能

- 緊急連絡先を登録、削除する機能
- ~~設定した帰還時間を過ぎた場合に、緊急連絡先へ自動通知する機能。~~
- ~~海上保安庁や最寄りの港の連絡先情報をアプリ内で提供。~~

### 9. フィードバックとコミュニティ機能（検討項目）

- ~~ユーザーからのフィードバック収集機能。~~
- ~~安全に関する知見や経験を共有するコミュニティスペース。~~
