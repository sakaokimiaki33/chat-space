## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false|
|password|string|null: false|

### Association
- has_many :groups, through: :user_groups
- has_many :user_groups
- has_many :messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|string||
|group|references|null: false,foreign_key:true|
|user|references|null: false, foreign_key:true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
has_many :users, through: :user_groups
has_many :user_groups
has_many :messages


## user_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group|references|null: false,foreign_key:true|
|user|references|null: false, foreign_key:true|

### Association
- belong_to :user
- belong_to :group