# DB 設計

## users table

| Column             | Type   | Options     |
|--------------------|--------|-------------|
| username           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

* has_many :donations
* has_many :donates
* has_many :comments


## donations table

| Column       | Type       | Options           |
|--------------|------------|-------------------|
| title        | string     | null: false       |
| category_id  | integer    | null: false       |
| continent_id | integer    | null: false       |
| country_id   | integer    | null: false       |
| description  | text       | null: false       |
| target       | integer    | null: false       |
| possible     | text       | null: false       |
| user         | references | foreign_key: true |

### Association

* belongs_to :user
* has_many :donates
* has_many :comments


## donate table

| Column   | Type       | Options           |
|----------|------------|-------------------|
| donation | references | foreign_key: true |
| user     | references | foreign_key: true |

### Association

* belongs_to :user
* belongs_to :donation
* has_one :address


## address table

| Column        | Type       | Options           |
|---------------|------------|-------------------|
| name          | string     | null: false       |
| sur_name      | string     | null: false       |
| postal_code   | string     | null: false       |
| prefecture_id | integer    | null: false       |
| city          | string     | null: false       |
| house_number  | string     | null: false       |
| building      | string     |                   |
| tell          | string     | null: false       |
| donate        | references | foreign_key: true |

### Association

* belongs_to :donate


## comment table

| Column   | Type       | Options           |
|----------|------------|-------------------|
| comment  | references | foreign_key: true |
| user     | references | foreign_key: true |

### Association

* belongs_to :user
* belongs_to :donation