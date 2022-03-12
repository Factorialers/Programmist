# Users

## User

ユーザーに関するオブジェクト型。

### Definition

```graphql
type User {
  id: ID!
  name: String!
  email: String
  emailVerified: Boolean!
  avatar: String!
  createdAt: Int!
  lastLoginAt: Int!
}
```

|フィールド|引数|返り値|認証|備考|
|-|-|-|-|-|
|id|None|ID!|不要|Firebase Authenticationで認証されたユーザーのuid。|
|name|None|String!|不要|ユーザー登録時にユーザーによって指定されたニックネーム。|
|email|None|String!|不要|Firebase Authenticationに使用されたメールアドレス。|
|emailVerified|None|Boolean!|不要|メールによる登録時、メールが確認されたか否か。|
|avatar|None|String!|不要|Firebase Storageかサードパーティによって保存されたユーザーアイコンのURL。|
|createdAt|None|Int!|不要|ユーザー登録が行われたUNIX時間。|
|lastLoginAt|None|Int!|不要|ユーザーが最後にログインしたUNIX時間。|

## NewUser

新規のユーザーをDBに登録する際に必要となる入力型。

### Definition

```graphql
input NewUser {
  name: String!
  avatar: String
}
```

|フィールド|引数|返り値|認証|備考|
|-|-|-|-|-|
|name|None|String!|不要|ユーザー登録時にユーザーによって指定されたニックネーム。|
|avatar|None|String|不要|Firebase Storageかサードパーティによって保存されたユーザーアイコンのURL。|