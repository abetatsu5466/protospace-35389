# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | not: null   |
| email    | string | not: null   |
| password | string | not: null   |
| profile  | text   | not: null   |
| occupation| text  | not: null   |
| position  | text   | not: null   |

### Association

- has_many :comments
- has_many :users , through: comments
- has_many :prototypes

## comments テーブル

| Column  | Type       | Options                        |
| ------- | ---------- |-- ---------------------------- |
| text    | text     |  not: null                       |
| user    | references |--------------------------- |
| prototype   | references | --------------------------- |

### Association

- belongs_to :prototypes
- belongs_to :users

## prototypes テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| title   | string | not: null |
| catch_copy| text | not: null |
| concept | text | not: null|
| image| ActiveStorage | ---------------------------|
| user | references | ---------------------------|

### Association

- has_many :users
- has_many :users, through: room_users
- has_many :messages