# version
インスタンスバージョンAPI

## エンドポイント一覧
常時公開エンドポイントです.  
認証は必要ありません.

| 絶対パス     | メソッド  | パラメータ | 備考             |
|----------|-------|-------|----------------|
| /version | GET   |       | インスタンスバージョンの取得 |

-----

### GET /server-info
インスタンスバージョンの取得

#### Response

##### 200 - found (application/json)
`revision` はローカルの最終コミットハッシュです.
```json
{
  "version": "Oshavery v0.1.5",
  "revision": "a2e125c1"
}
```
