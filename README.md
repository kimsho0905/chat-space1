# README


# Chat-Space DB設計
## users table
|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|nickname|string|null: false, unique: true|
### Association
- has_many :messages
- has_many :users_groups
- has_many :groups, through: users_groups

## messages table
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users_groups
- has_many :users, through: users_groups

## users_groups table
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
belongs_to :user
belongs_to :group