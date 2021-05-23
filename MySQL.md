---
tags:
    - DataBase
---

# MySQLモニタの起動

mysql -u root -p

# ユーザー関連
## ユーザー一覧

select user, host from mysql.user;

## 現在データベースに接続してるユーザー名

select current_user();

## ユーザーに設定されている権限を確認する

SHOW GRANTS FOR user@localhost

## ユーザー作成

CREATE USER user IDENTIFIED BY 'auth_string'

auth_stringはパスワードに置き換える．

userはユーザー名を入れる，書式はuser_name@host_nameという形にする．
指定したホストから指定したユーザー名でログインした場合だけ接続できる，という考え方である．

例えばthreecode@localhostみたいな

https://www.dbonline.jp/mysql/user/index1.html

## ユーザーに特定のデータベースに対する権限を与える

grant create on threecode_db.* to threecode@localhost;

この場合だとcreateの権限を与えている．createをselectにしたらselectの権限を与える．



# データベース関連

## データベース一覧

show databases;

## データベース作成

create database mydb;

## データベースを使う

use db_name;

## テーブル一覧

SHOW TABLES FROM table_name;

## テーブルの型を表示
show columns from table_name;

## 

