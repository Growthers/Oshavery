# Channels
チャンネルAPI

## エンドポイント一覧
**すべてのエンドポイントで認証が必須です**

| 絶対パス                                   | メソッド   | パラメータ                         | 備考          |
|----------------------------------------|--------|-------------------------------|-------------|
| /guilds/{guildId}/channels             | GET    | uuid v4 {guildId}             | チャンネルリストの取得 |
| /guilds/{guildId}/channels/{channelId} | PATCH  | uuid v4 {guildId},{channelId} | チャンネル情報の変更  |
| /guilds/{guildId}/channels/{channelId} | DELETE | uuid v4 {guildId},{channelId} | チャンネルの削除    |
| /guilds/{guildId}/channels             | POST   | none                          | チャンネルを作成    |

-----

### GET /guilds/{guildId}
チャンネルリストの取得

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| guildId | uuid_v4 | yes |

#### Response

##### 200 - found (application/json)
```json
[
    {
      "id": "8cebe4ae-98fd-4d9d-afb1-ad7dc8ec0f13",
      "channel_name": "general",
      "channel_topics": "main channel",
      "channel_type": "TEXT",
      "channel_position": 0,
      "creator_id": "be4a01db-4b14-4902-871d-41024170aa5c"
    }
]
```

------

### PATCH /guilds/{guildId}
チャンネル情報の変更
#### Request Body (application/json)
```json
{
  "name": "string",
  "position": 0,
  "topic": "string"
}
```

#### Response
##### 204 - No Content
##### 400 - Bad Request
##### 403 - Forbidden

-------

### DELETE /guilds/{guildId}/channels/{channelId}
チャンネルの削除

| パラメーター名   | データ型    | 必須か |
|-----------|---------|-----|
| guildId   | uuid_v4 | yes |
| channelId | uuid_v4 | yes |

#### Response
##### 204 - No Content
##### 400 - Bad Request
##### 403 - Forbidden

------

### POST /guilds
ギルドの作成

#### Request Body (application/json)
```json
{
  "channel_name": "string",
  "channel_topics": "string",
  "channel_type": "string",
  "channel_position": 0
}
```

#### Response
###### 200 - OK (application/json)
```json
    {
  "id": "8cebe4ae-98fd-4d9d-afb1-ad7dc8ec0f13",
  "channel_name": "general",
  "channel_topics": "main channel",
  "channel_type": "HOME",
  "channel_position": 0,
  "creator_id": "be4a01db-4b14-4902-871d-41024170aa5c"
}
```
