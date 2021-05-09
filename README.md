# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| --------           | ------ | ----------- |
| email              | string | null: false |
| encrypted_password | string | null: false |
| name               | string | null: false |
| family_name        | string | null: false |
| first_name         | string | null: false |
| family_name_kana   | string | null: false |
| first_name_kana    | string | null: false |

### Association
- has_many :seller_items, foreign_key: true
- has_many :buyer_items, foreign_key :true

## addresses テーブル
| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| post_code         | string | null: false |
| prefecture        | string | null: false |
| city              | string | null: false |
| street            | string | null: false |
| building          | string |             |
| phone_number      | string | null: false |

### Association
- belongs_to :users
- has_one :item_managements

## item_managements テーブル
| Column            | Type   | Options                        |
| --------          | ------ | -----------                    |
| buyer_id          | string | null: false, foreign_key: true |
| item_id           | string | null: false, foreign_key: true |
 
### Association
- belongs_to :items
- belongs_to :users

## items テーブル
| Column            | Type       | Options                        |
| --------          | ------     | -----------                    |
| name              | string     | null: false                    |
| price             | integer    | null: false                    |
| description       | text       | null: false                    |
| item_status       | string     | null: false                    |
| postage_type      | string     | null: false                    |
| postage_payer     | string     | null: false                    |
| category          | integer    | null: false                    |
| brand             | integer    |                                |
| seller_prefecture | string     | null: false                    |

### Association
- belongs_to :user dependent: :destroy