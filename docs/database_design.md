# データ設計

## モデル
- User
- Plant
- GrowthRecord

---

## モデルの関係
### User

- 複数のPlantを持つ

### Plant
- 一人のUserに属する
- 複数のGrowthRecordを持つ

### GrowthRecord
- 一つのPlantに属する

---

# テーブル設計
## usersテーブル

| カラム名 | 型 | 制約・説明 |
|----------|---------|-----------------------------|
| id | bigint | 主キー |
| name | string | ユーザー名 |
| email | string | メールアドレス |
| encrypted_password | string | パスワード |

---

## plantsテーブル

| カラム名 | 型 | 制約・説明 |
|----------|---------|-----------------------------|
| id | bigint | 主キー|
| user_id | bigint | users.idを参照する外部キー |
| name | string | 植物名 |
| variety | string | 品種名 |
| description | text | 植物の説明 |


---

## growth_recordsテーブル

| カラム名 | 型 | 制約・説明 |
|----------|---------|-----------------------------|
| id | bigint | 主キー |
| plant_id | bigint | plants.idを参照する外部キー |
| recorded_on | date | 記録日 |
| memo | text | 育成メモ |

## 画像
### Active Storage

画像ファイルはRailsのActive Storageで管理する。

- Plantは代表画像を1枚持つ
- GrowthRecordは成長記録画像を1枚持つ

画像データは plants テーブルや growth_records テーブルには保存されず、Active Storage用のテーブルで管理される。
