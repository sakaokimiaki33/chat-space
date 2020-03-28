## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key:true,unique: true,add_index|
|username|text|null: false, foreign_key:true,unique: true,add_index|
|emailaddress|string|null: false,unique: true|
|password|integer|null: false,unique: true|

### Association
- has_many :groups, through: :group
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
- has_many :user

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|groupname|text|null: false,foreign_key:true,add_index|
|group_id|integer|null: false,foreign_key:true,unique: true,add_index|

### Association
has_many :users, through: :group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false,foreign_key:true,unique: true|
|menbername|text|null: false, foreign_key:true,unique: true|
|user_id|integer|null: false, foreign_key:true,unique: true|

### Association
- belong_to :users