# DB 設計

## users テーブル

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| name               | string              | null: false               |

### Association

* has_many :records
* has_many :comments

## records テーブル

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| time_count                          | string     | null: false                    |
| max_blood_pressure                  | text       | null: false                    |
| min_blood_pressure                  | text       | null: false                    |
| pulse                               | text       | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| content     | text       | null: false                    |
| prototype   | references | null: false, foreign_key: true |
| user        | references | null: false, foreign_key: true |

### Association

- belongs_to :record
- belongs_to :user