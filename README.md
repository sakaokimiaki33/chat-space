## userテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|

### Association
- has_many :group, through: :user_group
- has_many :user_group
- has_many :messages
- has_many :images

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false,add_index|
|image_id|integer|null: false,foreign_key:true|
|group_id|integer|null: false,foreign_key:true|
|user_id|integer|null: false, foreign_key:true|

### Association
- belongs_to :user
- belongs_to :group
- belongs_to :images

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
has_many :user, through: :user_group
has_many :user_group
has_many :messages
has_many :images


## user_groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false,foreign_key:true|
|user_id|integer|null: false, foreign_key:true|

### Association
- belong_to :user
- belong_to :group

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false,foreign_key:true|
|user_id|integer|null: false, foreign_key:true|

### Association
- belong_to :user
- belong_to :group