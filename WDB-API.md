# WDB-API
## アプリ仕様

* iOS App
* iOS10以上

#### チェックイン画面
* イベントIDを入力するしてイベントにチェックイン
* イベントの新規作成

#### イベント画面
* イベント情報と投稿された写真の一覧を表示
* イベントテーマの変更
* イベントにまつわる写真の投稿・削除
* たくさん写真をアップロードするとベルが鳴る（適当）
* スワイプしたり、振ったら楽しいことが起こる

#### 写真画面
* 写真の詳細情報の表示
* Instagramへのシェア（SNS連携）

## API仕様

* 非公開なSSKDsAPI
* 専用のモバイルアプリで利用
* 基本的には1画面1API
* HATEOAS


### エンドポイント設計

|目的|エンドポイント|メソッド|
|:--|:--|:--|
|イベントにチェックイン|`v1/checkin`|POST|
|イベントの新規登録|`v1/events`|POST|
|イベント画面情報取得|`v1/event/:id`|GET|
|特定の写真の取得|`v1/event/photos/:id`|GET|
|写真のアップロード|`v1/event/photos`|POST|
|写真の削除|`v1/event/photos/:id`|DELETE|


## バックエンド

### ネットワーク構成
https://github.com/mafmoff/WedBell/blob/master/WedBell.png

言語は、JavaScriptで統一するため、MEAN Stackを用いる。

#### APサーバ
* Nginx
* node.js + Express

#### DB on Instance
* MongoDB
* イベントIDの保持

#### S3
* 写真の保存
