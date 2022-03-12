# Roots

## Query

ルート型のひとつ。  
HTTPメソッドの内、GETを担う。

### Definition

```graphql
type Query {
  getUser: User!
  listUser(name: String!, start: Int = 0, range: Int = 50): [User!]!
}
```

|フィールド|引数|返り値|認証|備考|
|-|-|-|-|-|
|getUser|None|User!|必須|tokenに合致するUserを返す。|
|listUser|name, start, range|[User!]!|不要|nameに合致するUserのリストを、start番目のインデックスからrangeの長さだけ返す。|

### Example

#### getUser

##### Query

```graphql
query GetUser{
  getUser{
    id
    name
    email
    emailVerified
    avatar
    createdAt
    lastLoginAt
  }
}
```

##### Response

```json
{
  "data": {
    "getUser": {
      "id": "Y2GD70mmKVYsT9lh09tu9Kb0p3x1",
      "name": "yukarisann-lover",
      "email": "hogehoge@gmail.com",
      "emailVerified": false,
      "avatar": "firebasestorage.googleapis.com/v0/b/hogehoge_app.appspot.com/o/sys%2Fdefault_avatar.png?alt=media",
      "createdAt": 1646254771,
      "lastLoginAt": 1647066265
    }
  }
}
```

#### listUser

##### Query

```graphql
query ListUser($name: String!, $start: Int = 0, $range: Int = 50) {
  listUser(name: $name, start: $start, range: $range) {
    id
    name
    email
    emailVerified
    avatar
    createdAt
    lastLoginAt
  }
}
```

##### Response

```json
{
  "data": {
    "listUser": [
      {
        "id": "Y2GD70mmKVYsT9lh09tu9Kb0p3x1",
        "name": "yukarisann-lover",
        "email": "hogehoge@gmail.com",
        "emailVerified": false,
        "avatar": "firebasestorage.googleapis.com/v0/b/hogehoge_app.appspot.com/o/sys%2Fdefault_avatar.png?alt=media",
        "createdAt": 1646254771,
        "lastLoginAt": 1647066265
      },
      {
        "id": "LRMxJA4J2nMDClXfADIhAtlb3DG2",
        "name": "yukarisann-lover",
        "email": "foo@outlook.jp",
        "emailVerified": false,
        "avatar": "firebasestorage.googleapis.com/v0/b/hogehoge_app.appspot.com/o/sys%2Fdefault_avatar.png?alt=media",
        "createdAt": 1646383072,
        "lastLoginAt": 1647066287
      }
    ]
  }
}
```

## Mutation

ルート型のひとつ。  
HTTPメソッドの内、POST, PUT, DELETEを担う。

### Definition

```graphql
type Mutation {
  signUpedUser(newUser: NewUser!): User!
  deletedUser: User!
}
```

|フィールド|引数|返り値|認証|備考|
|-|-|-|-|-|
|signUpedUser|newUser|User!|必須|tokenに合致するUserをDBに登録する。|
|deletedUser|None|User!|必須|tokenに合致するUserの情報をDBから削除する。|

### Example

#### signUpedUser

##### Query

```graphql
mutation SignUpedUser($new_user: NewUser!) {
  signUpedUser(newUser: $new_user) {
    id
    name
    email
    emailVerified
    avatar
    createdAt
    lastLoginAt
  }
}
```

##### Response

```json
{
  "data": {
    "signUpedUser": {
      "id": "LRMxJA4J2nMDClXfADIhAtlb3DG2",
      "name": "yukarisann-lover",
      "email": "hogehoge@outlook.jp",
      "emailVerified": false,
      "avatar": "firebasestorage.googleapis.com/v0/b/hogehoge_app.appspot.com/o/sys%2Fdefault_avatar.png?alt=media",
      "createdAt": 1646383072,
      "lastLoginAt": 1647065188
    }
  }
}
```

#### deletedUser

##### Query

```graphql
mutation DeletedUser {
  deletedUser {
    id
    name
    email
    emailVerified
    avatar
    createdAt
    lastLoginAt
  }
}
```

##### Response

```json
{
  "data": {
    "deletedUser": {
      "id": "Y2GD70mmKVYsT9lh09tu9Kb0p3x1",
      "name": "yukarisann-lover",
      "email": "hogehoge@gmail.com",
      "emailVerified": false,
      "avatar": "firebasestorage.googleapis.com/v0/b/hogehoge_app.appspot.com/o/sys%2Fdefault_avatar.png?alt=media",
      "createdAt": 1646254771,
      "lastLoginAt": 1647066265
    }
  }
}
```