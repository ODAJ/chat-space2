# chat-space2
 
## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true,unique: true|
|email|string|null: false, unique: true|

### Association
- has_many :groups, through: :members
- has_many :members
- has_many :messages


## gropusテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true |

### Association
- has_many :users, through: :members
- has_many :messages
- has_many :members


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|user_id|references|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
