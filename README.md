# テーブル設計

## users テーブル
| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| email             | string | null: false |
| password          | string | null: false |
| name              | string | null: false |
| profile           | text   | null: false |
| occupation        | text   | null: false |
| user_image        | string |             |
| family_name       | string | null: false |
| first_name        | string | null: false |
| family_name_kana  | string | null: false |
| first_name_kana   | string | null: false |
| birth_day         | date   | null: false |
| post_code         | string | null: false |
| prefecture        | string | null: false |
| city              | string | null: false |
| adress            | string | null: false |
| building_name     | string |             |
| phone_number      | string |             |

### Association
- has_many :seller_items, foreign_key: true
- has_many :buyer_items, foreign_key :true
- has_one :credit_card, dependent :destroy

## credit_cards テーブル
| Column            | Type   | Options                        |
| --------          | ------ | -----------                    |
| user              | string | null: false, foreign_key: true |
| customer_id       | string | null: false                    |
| card_id           | string | null: false                    |

### Association
- belongs_to :user

## items テーブル
| Column           | Type       | Options                        |
| --------         | ------     | -----------                    |
| name             | string     | null: false                    |
| price            | string     | null: false                    |
| description      | string     | null: false                    |
| item_conditions  | string     | null: false                    |
| postage_types    | string     | null: false                    |
| postage_payers   | string     | null: false                    |
| seller           | references | null: false, foreign_key:true  |
| buyer            | references | null: false, foreign_key:true  |
| category         | integer    | null: false                    |
| brand            | integer    |                                |

### Association
- belongs_to :user dependent: :destroy
- has_many :item_images dependent: :destroy
- belongs_to :category
- belongs_to :brand

## items_images
| Column        | Type   | Options     |
| --------      | ------ | ----------- |
| items_images  | string | null: false |
| url           | string | null: false |
#### Association
- belongs_to :items

## postage_types
| Column        | Type   | Options     |
| --------      | ------ | ----------- |
| postage_types | string | null: false |

#### Association
- has_many :items

## postage_players
| Column           | Type   | Options     |
| --------         | ------ | ----------- |
| postage_players | string | null: false |

#### Association
- has_many :items

## brands テーブル
| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| name              | string | null: false |

### Association
- has_many :items

## categories テーブル
| Column            | Type   | Options     |
| --------          | ------ | ----------- |
| name              | string | null: false |
| ancestry          | string |             |

### Association
- has_many :items