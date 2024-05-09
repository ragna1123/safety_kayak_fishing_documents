# 技術選定

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

- ActionMailer(メール送信)
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
