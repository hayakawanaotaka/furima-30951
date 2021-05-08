# テーブル設計

## users テーブル

| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| email             | string | null: false |
| password          | string | null: false |
| name              | string | null: false |
| family_name       | string | null: false |
| first_name        | string | null: false |
| family_name_kana  | string | null: false |
| first_name_kana   | string | null: false |
| birth_day         | date   | null: false |

### Association
- has_many :seller_items, foreign_key: true
- has_many :buyer_items, foreign_key :true
- has_one :credit_card, dependent :destroy

## addresses テーブル
| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| post_code         | string | null: false |
| prefecture        | string | null: false |
| city              | string | null: false |
| street            | string | null: false |
| building_name     | string |             |
| phone_number      | string |             |

### Association
- belongs_to :users

## items テーブル
| Column           | Type       | Options                        |
| --------         | ------     | -----------                    |
| name             | string     | null: false                    |
| price            | integer    | null: false                    |
| description      | text       | null: false                    |
| item_status      | string     | null: false                    |
| postage_types    | string     | null: false                    |
| postage_payers   | string     | null: false                    |
| category         | integer    | null: false                    |
| brand            | integer    |                                |

### Association
- belongs_to :user dependent: :destroy
- has_many :item_images dependent: :destroy