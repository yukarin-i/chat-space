
# chat-space  DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|
### Association
- has_many :groups
- has_many :messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string||
|body|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

### groupテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|text||
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :users
- has_many :messages



## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user