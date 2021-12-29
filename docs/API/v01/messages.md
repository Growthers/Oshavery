# Guilds
ギルドAPI

## エンドポイント一覧
**すべてのエンドポイントで認証が必須です**

| 絶対パス                                       | メソッド   | パスパラメータ                         | 備考              |
|--------------------------------------------|--------|---------------------------------|-----------------|
| /channels/{channelId}/messages             | GET    | uuid v4 {channelId}             | チャンネル内のメッセージを取得 |
| /channels/{channelId}/messages             | POST   | uuid v4 {channelId}             | メッセージを投稿        |
| /channels/{channelId}/messages/{messageId} | GET    | uuid v4 {channelId},{messageId} | メッセージの取得        |
| /channels/{channelId}/messages/{messageId} | PUT    | uuid v4 {channelId},{messageId} | メッセージの編集        |
| /channels/{channelId}/messages/{messageId} | DELETE | uuid v4 {channelId},{messageId} | メッセージの削除        |

-----

### GET /channels/{channelId}/messages
チャンネル内のメッセージを取得

| パラメーター名   | データ型    | 必須か | パラーメーター種類 |
|-----------|---------|-----|-----------|
| channelId | uuid_v4 | yes | path      |
| limit     | number  | yes | query     |
| before    | uuid_v4 | yes | query     |

#### Response

##### 200 - found (application/json)
`edited_timestamp` は更新されていない場合 `timestamp` と同じものが入ります
```json
[
  {
    "id": "642b8097-d4e4-4d02-b204-81a7d229508c",
    "timestamp": "2021-12-05T06:22:37.700Z",
    "author": {
      "id": "be4a01db-4b14-4902-871d-41024170aa5c",
      "name": "Chihiro",
      "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
      "bot": false,
      "state": 0
    },
    "content": "Hello world!",
    "guild_id": "",
    "channel_id": "",
    "edited_timestamp": "string"
  }
]
```

------

### POST /channels/{channelId}/messages
メッセージの投稿

#### Request Body (application/json)
```json
{
  "content": ""
}
```

#### Response
##### 201 - Created
```json
{
  "id": "642b8097-d4e4-4d02-b204-81a7d229508c",
  "timestamp": "2021-12-05T06:22:37.700Z",
  "author": {
    "id": "be4a01db-4b14-4902-871d-41024170aa5c",
    "name": "Chihiro",
    "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
    "bot": false,
    "state": 0
  },
  "content": "Hello world!",
  "guild_id": "bb469c49-6828-4a94-9892-a8849a314309",
  "channel_id": "cda9ec60-8309-4ced-8f93-e895192236dc",
  "edited_timestamp": "2021-12-05T06:22:37.700Z"
}
```
##### 400 - Bad Request
##### 403 - Forbidden

-------

### PUT /channels/{channelId}/messages/{messageId}
メッセージを編集

| パラメーター名   | データ型    | 必須か |
|-----------|---------|-----|
| guildId   | uuid_v4 | yes |
| messageId | uuid_v4 | yes |


#### Request Body (application/json)
```json
{
  "content": "Hello, World!"
}
```

#### Response
##### 201 - Created
##### 403 - Forbidden
##### 404 - Not Found

-------

### DELETE /channels/{channelId}/messages/{messageId}
メッセージの削除

| パラメーター名   | データ型    | 必須か |
|-----------|---------|-----|
| guildId   | uuid_v4 | yes |
| messageId | uuid_v4 | yes |


#### Response
###### 204 - No Content
###### 403 - Forbidden
###### 404 - Not Found
```
