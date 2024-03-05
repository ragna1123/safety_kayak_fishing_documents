# 技術選定

## フロントエンド

### フレームワーク

- Next.js

### ライブラリ

- TypeScript

### CSS

- TailwindCSS

## バックエンド

### フレームワーク

- Ruby on Rails(API)

### ライブラリ

- ActionMailer(メール送信)
- JWT(認証)
- sideqik(時刻で処理を起動させる※今回はメール送信に使用)

## データベース

- Postglesql または MySQL

## 外部 API

### 地図

- GoogleMap(地図) https://developers.google.com/maps?hl=ja

### 天気予報候補

- yhaoo!気象情報
  https://developer.yahoo.co.jp/webapi/map/openlocalplatform/v1/weather.html
- OpenWeatherMap API
  https://openweathermap.org/
- Weatherstack API
  https://weatherstack.com/
- windy トライアル版(天気、風、波予報) https://api.windy.com/  
  ※多少の精度誤差と 500 回/day のアクセス制限

### 潮位

- 日本沿岸 736 港の潮汐表 https://tide736.net/