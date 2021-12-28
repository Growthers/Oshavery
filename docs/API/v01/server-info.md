# Server_info
インスタンス情報API

## エンドポイント一覧
**一部のエンドポイントで認証が必須です**

| 絶対パス         | メソッド  | パラメータ | 備考                |
|--------------|-------|-------|-------------------|
| /server-info | GET   |       | インスタンス情報の取得       |
| /server-info | POST  |       | インスタンス情報の設定(認証必須) |
| /server-info | PATCH |       | インスタンス情報の更新(認証必須) |

-----

### GET /server-info
インスタンス情報の取得

#### Response

##### 200 - found (application/json)
```json
{
  "instance_name": "Working Space-123",
  "user_count": 10,
  "message_count": 100,
  "admin": {
    "account": "Chihiro",
    "mail": "chihiro@example.com"
  },
  "tos": "https://example.com/tos",
  "privacy_policy": "https://example.com/policy"
}
```

------

### POST /server-info
インスタンス情報の設定(認証必須)

#### Request Body (application/json)
```json
{
  "instance_name": "Working Space-123",
  "admin": {
    "account": "Chihiro",
    "mail": "chihiro@example.com"
  },
  "tos": "https://example.com/tos",
  "privacy_policy": "https://example.com/policy"
}
```

#### Response
##### 200 - Created (application/json)
```json
{
  "instance_name": "Working Space-123",
  "user_count": 1,
  "message_count": 0,
  "admin": {
    "account": "Chihiro",
    "mail": "chihiro@example.com"
  },
  "tos": "https://example.com/tos",
  "privacy_policy": "https://example.com/policy"
}
```
##### 400 - Bad Request
##### 403 - Forbidden

-------

### PATCH /server-info
インスタンス情報の更新(認証必須)

#### Request Body (application/json)
```json
{
  "instance_name": "Working Space-123",
  "admin": {
    "account": "Chihiro",
    "mail": "chihiro@example.com"
  },
  "tos": "https://example.com/tos",
  "privacy_policy": "https://example.com/policy"
}
```

#### Response
##### 200 - Created (application/json)
```json
{
  "instance_name": "Working Space-123",
  "user_count": 1,
  "message_count": 0,
  "admin": {
    "account": "Chihiro",
    "mail": "chihiro@example.com"
  },
  "tos": "https://example.com/tos",
  "privacy_policy": "https://example.com/policy"
}
```
##### 400 - Bad Request
##### 403 - Forbidden

---