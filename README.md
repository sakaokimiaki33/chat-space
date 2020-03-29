## userテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false|
|password|string|null: false|

### Association
- has_many :group, through: :u-g
- has_many :u-g
- has_many :messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false,add_index|
|image|string||
|group_id|integer|null: false,foreign_key:true|
|user_id|integer|null: false, foreign_key:true|

### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false|

### Association
has_many :user, through: :u-g
has_many :u-g


## u-gテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false,foreign_key:true|
|user_id|integer|null: false, foreign_key:true|

### Association
- belong_to :user
- belong_to :group