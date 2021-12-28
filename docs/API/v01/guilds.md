# Guilds
ギルドAPI  

## エンドポイント一覧
**すべてのエンドポイントで認証が必須です**

| 絶対パス                               | メソッド   | パラメータ                      | 備考              |
|------------------------------------|--------|----------------------------|-----------------|
| /guilds/{guildId}                  | GET    | uuid v4 {guildId}          | ギルド情報の取得        |
| /guilds/{guildId}                  | PATCH  | uuid v4 {guildId}          | ギルド情報の変更        |
| /guilds/{guildId}                  | DELETE | uuid v4 {guildId}          | ギルドの削除          |
| /guilds/{guildId}/members          | GET    | uuid v4 {guildId}          | ギルドメンバーの取得      |
| /guilds/{guildId}/members/{userId} | GET    | uuid v4 {guildId},{userId} | 特定のギルドメンバー情報の取得 |
| /guilds/{guildId}/members/{userId} | PATCH  | uuid v4 {guildId},{userId} | 特定のギルドメンバー情報の変更 |
| /guilds                            | POST   | none                       | ギルドを作成          |

-----

### GET /guilds/{guildId}

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| guildId | uuid_v4 | yes |

#### Response

##### 200 - found (application/json)
```json
{
  "id": "a4cca42b-29ea-44f5-9aa2-4da654a1147b",
  "name": "Project",
  "topic": "Guild for Project",
  "icon": "https://example.com/media/a4cca42b-29ea-44f5-9aa2-4da654a1147b",
  "owner_id": "Chihiro",
  "users": [
    {
      "id": "be4a01db-4b14-4902-871d-41024170aa5c",
      "name": "Chihiro",
      "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
      "bot": false,
      "state": 0
    }
  ],
  "channels": [
    {
      "id": "8cebe4ae-98fd-4d9d-afb1-ad7dc8ec0f13",
      "channel_name": "general",
      "channel_topics": "main channel",
      "channel_type": "TEXT",
      "channel_position": 0,
      "creator_id": "be4a01db-4b14-4902-871d-41024170aa5c"
    }
  ]
}
```

------

### PATCH /guilds/{guildId}
ギルド情報の更新

#### Request Body (application/json)
```json
{
  "name": "string",
  "icon": "string",
  "owner_id": "string"
}
```

#### Response
##### 204 - No Content
##### 400 - Bad Request
##### 403 - Forbidden

------

### DELETE /guilds/{guildId}
ギルドの削除

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| guildId | uuid_v4 | yes |

#### Response
##### 204 - No Content
##### 400 - Bad Request
##### 403 - Forbidden

------

### GET /guilds/{guildId}/members
ギルドメンバーの取得

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| guildId | uuid_v4 | yes |
| userId  | uuid_v4 | yes |

#### Response

##### 200 - found (application/json)
```json
[
  {
    "id": "be4a01db-4b14-4902-871d-41024170aa5c",
    "name": "Chihiro",
    "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
    "bot": false,
    "state": 0
  }
]
```

-------

### PUT /guilds/{guildId}/members/{userId}
特定のユーザー情報を編集

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| guildId | uuid_v4 | yes |


#### Request Body (application/json)
```json
{
  "nick": "Ch"
}
```

#### Response
##### 201 - Created
##### 403 - Forbidden

-------

### POST /guilds
ギルドの作成

#### Request Body (application/json)
```json
{
  "guild_name": "Project",
  "guild_topics": "Guild for Project"
}
```

#### Response
###### 200 - OK (application/json)
```json
{
  "id": "a4cca42b-29ea-44f5-9aa2-4da654a1147b",
  "name": "Project",
  "topic": "Guild for Project",
  "icon": "https://example.com/media/a4cca42b-29ea-44f5-9aa2-4da654a1147b",
  "owner_id": "Chihiro",
  "users": [
    {
      "id": "be4a01db-4b14-4902-871d-41024170aa5c",
      "name": "Chihiro",
      "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
      "bot": false,
      "state": 0
    }
  ],
  "channels": [
    {
      "id": "8cebe4ae-98fd-4d9d-afb1-ad7dc8ec0f13",
      "channel_name": "general",
      "channel_topics": "main channel",
      "channel_type": "HOME",
      "channel_position": 0,
      "creator_id": "be4a01db-4b14-4902-871d-41024170aa5c"
    }
  ]
}
```
