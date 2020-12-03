#　MyMekeupPouch
アプリケーション名

## アプリケーションの概要
ユーザー登録
ログインしているユーザーはアイテムの登録を行える
化粧ポーチの観覧機能
ポーチの作成 ポーチ内にはアイテムを追加し一覧として表示できる

## URL


## テスト用アカウント


## 利用方法
投稿された化粧ポーチの観覧を行える

ログインしているユーザーは自分の化粧品を登録でき
登録された化粧品を化粧ポーチ内に入れ投稿できる
用途に合わせた化粧ポーチを投稿できる

投稿したユーザーは自分の化粧ポーチの編集を行える

## 目指した課題解決
用途に合わせた化粧ポーチの中身を確認でき
出掛けるときなどに持ち歩くおすすめの化粧品の紹介や
シーンに合わせどういう内容の化粧品を持ち歩けば便利か等を確認できる
化粧ポーチ内の予算を確認できる

## 実装した機能について
ユーザー登録するためのusersテーブルの作成
化粧品を登録するためのitemsテーブルの作成
登録した化粧品を入れ投稿できるpouchsテーブルの作成

## 実装予定の機能
likeボタンの追加
お気に入り登録機能

## データベースの設計図


## ローカル環境での動作方法


# テーブル設計

## users テーブル

| Column             | Type    | Options                  |
| ------------------ | ------- | ------------------------ |
| nickname           | string  | null: false              |
| email              | string  | null:false, unique: true |
| encrypted_password | string  | null: false              |
| age_id             | integer | null: false              |
| profession_id      | string  | null: false              |

### Association

- has_many :items
- has_many :pouchs

## items テーブル

| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| name          | string     | null: false       |
| maker         | string     | null: false       |
| category_id   | integer    | null: false       |
| price         | string     |                   |

### Association

- belongs_to :user
- has_many :pouchs

## pouchs テーブル

| Column | Type       | Options           |
| ------ | ---------- | ----------------- |
| title  | strung     | null: false       |
| user   | references | foreign_key :true |
| use_id | integer    | null: false       |
| item   | references | foreign_key :true |
| text   | text       |                   |


### Association

- belongs_to :user
- belongs_to :item
