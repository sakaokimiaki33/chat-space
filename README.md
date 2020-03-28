# README
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key:true,unique: true,add_index|
|username|text|null: false, foreign_key:true,unique: true,add_index|
|emailaddress|string|null: false,unique: true|
|password|integer|null: false,unique: true|

### Association
- has_many :messages, through: :groups
- has_many :groups
- has_many :messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|message_id|string|null: false,foreign_key:true,unique: true,add_index|
|text|text|null: false,add_index|
|image_id|integer|foreign_key:true|
|group_id|integer|null: false,foreign_key:true,unique: true,add_index|
|user_id|integer|null: false, foreign_key:true,unique: true,add_index|
# timestampはデフォルトで生成される

### Association
- has_many :users, through: :groups
- has_many :groups
- has_many :users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|groupname|text|null: false,foreign_key:true,add_index|
|group_id|integer|null: false,foreign_key:true,unique: true,add_index|

### Association
- has_many :groups
- has_many :users

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image_id|string|null: false,foreign_key:true,unique: true,add_index|
|group_id|integer|null: false,foreign_key:true,unique: true|
|user_id|integer|null: false, foreign_key:true,unique: true|

### Association
- belong_to :users