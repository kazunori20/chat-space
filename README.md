# README
usersテーブル
|Column|Type  |Options                          |
|:----:|:----:|:-------------------------------:|
|name  |string|index:true,nell:false,unique:true|
|mail  |string|nell:false                       |
### Association
- has_many:groups,througt:members
- has_many:messages
- has_many:members

messageテーブル
|Column  |Type  |Options                                        |
|:------:|:----:|:---------------------------------------------:|
|body    |text  |user_id integer null: false, foreign_key: true |
|image   |string|group_id integer null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

groupテーブル
|Column|Type  |Options                  |
|:----:|:----:|:-----------------------:|
|name  |string|null: false, unique: true|
### Association
- has_many:members
- has_many :users, through: groups_users
- has_many :messages

groups_usersテーブル
|Column|Type     |Options                       |
|:------:|:-----:|:----------------------------:|
|user_id|integer |null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user
