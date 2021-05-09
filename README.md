# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| --------           | ------ | -----------               |
| email              | string | null: false, unipue: true |
| encrypted_password | string | null: false               |
| name               | string | null: false               |
| family_name        | string | null: false               |
| first_name         | string | null: false               |
| family_name_kana   | string | null: false               |
| first_name_kana    | string | null: false               |
| birth_day          | string | null: false               |

### Association
- has_many :items
- has_one :item_manadgement

## addresses テーブル
| Column            | Type       | Options                        |
| --------          | ------     | -----------                    |
| post_code         | string     | null: false                    |
| prefecture_id     | integer    | null: false                    |
| city              | string     | null: false                    |
| street            | string     | null: false                    |
| building          | string     |                                |
| phone_number      | string     | null: false                    |
| item_management   | references | null: false, foreign_key: ture |

### Association
- belongs_to :user

## item_managements テーブル
| Column            | Type       | Options                        |
| --------          | ------     | -----------                    |
| user              | references | null: false, foreign_key: true |
| item              | references | null: false, foreign_key: true |
 
### Association
- belongs_to :item
- belongs_to :user
- has_one :address

## items テーブル
| Column            | Type       | Options                        |
| --------          | ------     | -----------                    |
| name              | string     | null: false                    |
| price             | integer    | null: false                    |
| description       | text       | null: false                    |
| item_status       | integer    | null: false                    |
| delivery_fee      | integer    | null: false                    |
| delivery_day      | integer    | null: false                    |
| category          | integer    | null: false                    |
| seller_prefecture | integer    | null: false                    |
| user              | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_one :item_management