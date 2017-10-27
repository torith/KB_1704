# FACECARD

[![Facecard](https://github.com/jphacks/KB_1704/blob/master/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202017-10-22%2013.13.31.png)](https://youtu.be/94qj7hEdMgs)

## 製品概要
### BusiTech = Business × Tech
顔認証で名刺交換を楽しく。ビジネスの場において名刺交換は人間関係を構築する最初のステップです。FACECARDを使うと紙の名刺を使う必要はもうありません。相手の顔をスマートフォンで認証すれば相手の連絡先が入手できます。もっとカジュアルに笑顔の溢れる第一印象を与えることができます。

### 背景
- 名刺交換って古くないですか？
- 名刺交換って堅苦しくないですか？
- 名刺って管理面倒じゃないですか？

### 製品説明
顔認証で名刺交換をするサービスです。相手の顔にスマートフォンをかざすだけで名刺交換ができます。デジタルで個人情報を管理し、サービスが指定する表情をリアルタイムで相手にしてもらうことで本人確認を行います。現時点では、全ユーザの情報を持っているサービス共通データベースから顔認識後、表情認証を用いて個人情報を取得することができます。つまり顔認証によるFacecard登録ができます。ユーザがサービス開始時のFacecard登録やユーザによるFacecard管理機能はまだ実装していません。

### 特長
#### 1. 顔認証で名刺交換
あらかじめ自分の顔画像とプロフィールをデータベースに登録しておけば、後はカメラで撮ってもらうだけ。撮影された顔と自分の顔画像を自動で照合し、その人が誰なのかを顔認証で判別します。お手軽に楽しく、自分をもっと知ってもらいやすくなります。

#### 2. 名刺のデジタル管理 (部分実装)
必要な情報はすべてデータベースに。世界中の人と出会っても、スマートフォン1つで管理できます。

#### 3. 表情認識で本人確認
もし自分の顔を勝手に撮られたら？そんな心配はいりません。あなたの顔を撮影すると、「表情」の指示が送られてきます。あなたがその表情をしない限り、相手にあなたのプロフィールを勝手に見られることはありません。コミュニケーションにも役立ちます。

### 解決出来ること
名刺のデジタル化。交換の簡単化。交換時の堅苦しさをなくし、お手軽に楽しく、自分をもっと知ってもらいやすくなります。

### 今後の展望
本サービスは、セキュリティ面や機能面(未実装点、エラー処理)で改善の余地があります。特にセキュリティ面はまだまだガバガバです。
また、本サービスがFacebookやLinkedInと統合されれば、全ユーザの情報を持っているサービス共通データベースがSNS情報と統合されFacecard登録の手間が省けます。

## 開発内容・開発技術
### 活用した技術
#### API・データ
スポンサーから提供されたAPI、製品などの外部技術
- AamazonWebService
  - EC2(インスタンスタイプ：x2.large)
  - S3
  - Lambda
  - API gateway
  - dynamo DB
- Microsoft Azure
  - Face API

#### フレームワーク・ライブラリ・モジュール
- Javascript
  - Node.js(フレームワーク)
  - http(モジュール)
  - url(モジュール)
  - fs(モジュール)
  - XMLHttpRequest(モジュー)
- iOS アプリサンプル
  - [github](https://github.com/awslabs/aws-sdk-ios-samples/tree/master/CognitoYourUserPools-Sample/Swift)
#### デバイス
- iPhone 6
### システムモデル
![Systemmodel](https://github.com/jphacks/KB_1704/blob/master/system.png)


### 研究内容・事前開発プロダクト（任意）
- 事前知識の学習
- 開発環境の構築

### 独自開発技術（Hack Dayで開発したもの）
#### 2日間に開発した独自の機能・技術
- iOS上で動くアプリケーションの開発
  - Swiftのサンプルプログラムを改良して開発。AWS上で展開するサーバと通信。
- サーバプログラム
  - Javascriptを用いたHTTPサーバを構築
  - モバイルデバイスから顔写真のURLなどをリクエストとして受取り、Azure Face APIへ渡す処理などを担当
  - Azure Face APIを利用し、顔写真からプロフィールをデータベースから取得し、モバイルデバイスへ返信
