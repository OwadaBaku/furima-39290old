
# アプリケーション名
Furima

# アプリケーション概要
フリマサイト（あとで修正）  

# URL
Renderによるデプロイ：  
https://furima-39290.onrender.com/
  
Basic認証：  
- ID:admin
- Pass:2222

# テスト用アカウント
### 購入者用
- メールアドレス:furimab@test.com
- パスワード:furimab1
### 購入用カード情報(PAYJPテスト用)
- 番号：4242424242424242
- 期限：???あとで
- セキュリティコード：123
-

#### 出品者用
- メールアドレス:furimap@test.com
- パスワード:furimap1

# 利用方法
# アプリケーションを作成した背景
# 洗い出した要件
## users テーブル

| Column             | Type   | Options                   |
| :----------------- | :----- | :------------------------ |
| nickname           | string | null: false, unique: true |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false, unique: true |
| last_name          | string | null: false               |
| first_name         | string | null: false               |
| last_name_kana     | string | null: false               |
| first_name_kana    | string | null: false               |
| birthday           | date   | null: false               |

#### Association

- has_many :items
- has_many :orders
- has_many :comments

### items テーブル

| Column           | Type       | Options                        |
| :--------------- | :--------- | :----------------------------- |
| user             | references | null: false, foreign_key: true |
| name             | string     | null: false                    |
| description      | text       | null: false                    |
| category_id      | integer    | null: false                    |
| item_status_id   | integer    | null: false                    |
| shipping_cost_id | integer    | null: false                    |
| prefecture_id    | integer    | null: false                    |
| shipping_date_id | integer    | null: false                    |
| price            | integer    | null: false                    |

#### Association

- belongs_to :user
- has_one :order
- has_many :comments

### orders テーブル

| Column | Type       | Options                        |
| :----- | :--------- | :----------------------------- |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

#### Association

- belongs_to :user
- belongs_to :item
- has_one :payment

### payments テーブル

| Column        | Type       | Options                        |
| :------------ | :--------- | :----------------------------- |
| orders        | references | null: false, foreign_key: true |
| postcode      | string     | null: false                    |
| prefecture_id | integer    | null: false                    |
| city          | string     | null: false                    |
| block         | string     | null: false                    |
| building      | string     |                                |
| phone_number  | string     | null: false                    |

#### Association

- belongs_to :order

### comments テーブル

| Column | Type       | Options                        |
| :----- | :--------- | :----------------------------- |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |
| text   | text       | null: false                    |

#### Association

- belongs_to :user
- belongs_to :item

# 実装した機能についての画像やGIFおよびその説明
# 実装予定の機能
# データベース設計
# 画面遷移図
# 開発環境
# ローカルでの動作方法
# 工夫したポイント


