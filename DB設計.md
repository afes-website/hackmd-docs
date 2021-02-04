###### tags: `GitHub`

# DB設計

## exhibitions

展示

| column   | type | descript                                |
| -------- | ---- | --------------------------------------- |
| id       | (PK) | 展示ID(=教室番号?)                      |
| type     |      | 展示種別(通常/フロンティア/飲食)        |
| name     | text | 展示名                                  |
| icon     |      | 画像(埋め込み?IDと同名にする方法もある) |
| descript | text | 展示説明                                |

## tickets

発行整理券
間にこれを挟んだほうが管理しやすい…よね?

| column     | type       | descript                   |
| ---------- | ---------- | -------------------------- |
| id         | (PK)       | 固有ID 連番?               |
| exhibition |            | 展示ID                     |
| name       | text       | 名前                       |
| descript   | text       | 説明                       |
| time       | (NULLABLE) | 開始時間(時間型整理券のみ) |

## reservation

予約整理券
ユーザに対して

| column | type | descript                  |
| ------ | ---- | ------------------------- |
| id     |      | 固有ID これで処理ができる |
| user   |      | 予約ユーザ                |
| ticket |      | 整理券ID                  |

## announcements

告知、通知
(プッシュかバッヂかをつける)

| column    | type | descript               |
| --------- | ---- | ---------------------- |
| id        | (PK) | 固有ID 連番?           |
| author    |      | 配信者                 |
| summary   | text | 要約(30文字程度?)      |
| content   | text | 内容                   |
| priority  |      | 重要度(情報,緊急 など) |
| timestamp |      | 配信時刻               |

## post_categories

カテゴリ

| column | type    | descript         |
| ------ | ------- | ---------------- |
| id     | varchar | カテゴリID ->URL |
| name   | text    | 名前             |

## posts

ブログ記事

| column      | type                     | descript                                     |
| ----------- | ------------------------ | -------------------------------------------- |
| id          | (PK)                     | 投稿ID 連番じゃないらしいよ                  |
| category    | varchar                  | カテゴリ                                     |
| author      |                          | 投稿者                                       |
| create_time |                          | 作成日時                                     |
| update_time |                          | 更新日時 (要る?)(更新は訂正程度にしてほしい) |
| title       | text                     | タイトル                                     |
| content     | `/(medium\|long\|)text/` | 記事本文                                     |

## stage_perfs

ステージパフォーマンス
リスト表示するだけかせいぜい検索かけるだけ

| column   | type | descript                                   |
| -------- | ---- | ------------------------------------------ |
| id       |      | これ要るかな いらない気がしている 一応追加 |
| name     |      | 名前                                       |
| time     |      | 開始時刻                                   |
| descript | text | 説明文                                     |

## votes

投票
問:訂正可能にするか?

| column              | type       | descript     |
| ------------------- | ---------- | ------------ |
| user                | (UNIQ?PK?) | 投票者       |
| timestamp           |            | 投票時刻     |
| exhibition_normal   |            | 通常展示応募 |
| exhibition_foods    |            | 飲食         |
| exhibition_frontier |            | フロンティア |
