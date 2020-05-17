# chat-spce DB設計

## groups_userテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## massagesテーブル
|Column|Type|Options|
|------|------|-----|
|body|text|
|image|string|
|group_id|integer|nnull: false, foreign_key: true|
|user_id|integer|null: false, foreing_key: true|
### Association
belongs_to :group
belongs_to :user

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
### Association
has_many :groups_users
has_many :users, through: groups_users
has_many :messages
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|password confirmation|string|null: false|
### Association
has_many :groups_users
has_many :groups, through: groups_users
has_many :messages
