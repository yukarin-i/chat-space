
# chat-space  DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false,  index:true|
### Association
- has_many :groups, through: :groups_users
- has_many :messages
- has_many :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string||
|body|text||
|user|reference|null: false, foreign_key: true|
|group|reference|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

### groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|text||
### Association
- has_many :users, through: :groups_users
- has_many :messages
- has_many :groups_users


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|group|reference|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user