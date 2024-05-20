# hostdb

[![License](https://img.shields.io/github/license/maphorie/hostdb)](https://github.com/maphorie/hostdb/blob/main/LICENSE)

ホストの情報(ホスト名，IPv4アドレス，IPv6アドレス，MACアドレス)をMongoDBデータベースで管理します．

## 必要なパッケージ

- Ruby
- mongo gem
- (MongoDBサーバ)

## データベースの設定

```text
use hosts

db.createUser( { user:  "ユーザ名",
                 pwd:   "パスワード",
                 roles: [ "readWrite", "dbAdmin" ] } )

db.createCollection( "hosts" )
```

## コマンド

### データベースオプション

| オプション | 説明                                    |
|------------|-----------------------------------------|
| `-h`       | MongoDBサーバのIPアドレスまたはホスト名 |
| `-P`       | MongoDBサーバのポート                   |
| `-u`       | ユーザ名                                |
| `-p`       | パスワード                              |
| `-d`       | データベース名                          |
| `-c`       | コレクション名                          |

### サブコマンド

#### list

ホストをリスト

```console
$ hostdb データベースオプション list
```

#### search

ホストの検索

```console
$ hostdb データベースオプション search クエリ
例
$ hostdb データベースオプション search host01
$ hostdb データベースオプション search 192.0.2.2
$ hostdb データベースオプション search 2001:db8::2
$ hostdb データベースオプション search 01:23:45:67:89:ab
```

#### add

ホストの追加

```console
$ hostdb データベースオプション add ホスト名 ...
例
$ hostdb データベースオプション add host01 192.0.2.2 2001:db8::2 01:23:45:67:89:ab
```

#### delete

ホストの削除

```console
$ hostdb データベースオプション delete ホスト名
例
$ hostdb データベースオプション delete host01
```
