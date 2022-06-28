開発用メモ<br>
TOP：app/views/recipes/index.html.erb
TOPのCSS：app/assets/stylesheets/recipes/index.css

# アプリ名
SpiceLife

# アプリ概要
- カレー限定のレシピ投稿サイト
- 自作のカレーのレシピを記録することで、次回以降のレシピに活かすことができる
- 他者のレシピを見ることで、どんなカレーを作るか迷った時、参考にできる

# 使用技術
- フロントエンド
HTML/CSS/JavaScript

- バックエンド
Ruby 2.6.5/Rails 6.0.3

- テスト基盤
RSpec 3.9/FactoryBot 4.10.0

- データベース
MySQL 5.7

- インフラ
Docker 20.10.7/Docker Compose 1.29.2
AWS(VPC, EC2, IAM, RDS, InternetGataway, SecurityGroup, Subnet, Route53, ALB, ACM, S3)
Nginx 1.15.8

# 要件定義
https://docs.google.com/spreadsheets/d/17XDD9jDpEw67a4_g1fXk-Ol8deqRRk42P69F3L1CBhI/edit#gid=982722306

# DB設計

## usersテーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

### Association

- has_many :

## Recipesテーブル

| Column             | Type    | Options                        |
| ------------------ | ------  | ------------------------------ |
| user_id            | integer | null: false, foreign_key: true |
| title              | string  | null: false                    |
| descriptions       | text    |                                |
| point              | text    |                                |

### Association

- has_many_attached :images

## Ingredientsテーブル

| Column             | Type    | Options                        |
| ------------------ | ------  | ------------------------------ |
| recipe_id          | integer | null: false, foreign_key: true |
| content            | string  |                                |
| quantity           | string  |                                |

### Association

- has_many :

## Favoritesテーブル
| Column             | Type    | Options                        |
| ------------------ | ------  | ------------------------------ |
| user_id            |         | null: false, foreign_key: true |
| recipe_id          |         | null: false, foreign_key: true |