# /users

ユーザーAPI

## エンドポイント一覧
**すべてのエンドポイントで認証が必須です**

| 絶対パス            | メソッド  | パラメータ            | 備考             |
|-----------------|-------|------------------|----------------|
| /users/{userId} | GET   | uuid v4 {userId} | 指定されたユーザーIDを返す |
| /users/{userId} | PATCH | uuid v4 {userId} | ユーザー情報を更新      |
| /users          | POST  | none             | ユーザーを登録        |
| /users          | GET   | none             | ユーザー一覧を取得      |
| /users/me       | GET   | none             | 自分のユーザー情報を取得   |
| /users/me       | PATCH | none             | 自分のユーザー情報を変更   |

------

### GET_/users/{userId}
指定されたIDのユーザー情報を返します  

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| userId  | uuid_v4 | yes |

#### Response 

#####  200 -  found (application/json)
```json
{ 
    "id": "be4a01db-4b14-4902-871d-41024170aa5c",
    "name": "Chihiro",
    "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
    "bot": false,
    "state": 0
} 
 ``` 
##### 404 - Not Found

----

### PATCH /users/{userId}
指定したIDのユーザー情報を更新

| パラメーター名 | データ型    | 必須か |
|---------|---------|-----|
| userId  | uuid_v4 | yes |

#### Request Body (application/json)
```json
{
  "name": "string"
}
```

#### Response
##### 204 - No Content
##### 400 - Bad Request

----

### POST /users
ユーザーを新規登録します

#### Request Body (application/json)
```json
{
  "name": "Chihiro",
  "password": "password"
}
```

#### Response
##### 201 - Created (application/json)
```json
{
  "id": "be4a01db-4b14-4902-871d-41024170aa5c",
  "name": "Chihiro",
  "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
  "bot": false,
  "state": 0
} 
```
##### 400 - Invalid Request
##### 409 - Conflict (すでに同名のユーザーが存在する場合)

----

### GET /users
登録されているすべてのユーザーを返す

#### Response (application/json)
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

----

### GET /users/me
アクセスしたユーザーのユーザー情報を返す

#### Response (application/json)

##### 200 - OK
```json
{
  "id": "be4a01db-4b14-4902-871d-41024170aa5c",
  "name": "Chihiro",
  "avatar": "https://example.com/media/be4a01db-4b14-4902-871d-41024170aa5c.png",
  "bot": true,
  "state": 0,
  "guilds": [
    {
      "id": "2599a1ae-88ff-4645-821c-59d21192be6a",
      "name": "Project",
      "topic": "Project guild",
      "icon": "https://example.com/media/2599a1ae-88ff-4645-821c-59d21192be6a.png",
      "owner_id": "be4a01db-4b14-4902-871d-41024170aa5c"
    }
  ]
}
```

----

### PATCH /users/me
アクセスしたユーザーのユーザー情報を変更

#### Request Body (application/json)
```json
{
  "name": "string"
}
```

#### Response
##### 204 - No Content
##### 400 - Bad Request

----
