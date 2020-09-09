# ストレージラインの選択
GCSのオブジェクトのストレージクラスの選択は以下を考慮して決定する
- アクセス頻度
- 料金

### 使用可能なストレージクラス
- Standard Storage
  - STANDARD
  - 最小保存期間　なし
  - リージョンで99.99%
  - 頻繁にアクセスされるデータや短期間のみ保管するデータに適している
- Nearline Storage
  - NEARLINE
  - 最小保存期間　30日
  - リージョンで99.9%
  - 読み取り、変更を月に1度程度のデータを保管するのに適している
- Coldline Storage
  - COLDLINE
  - 最小保存期間　90日
  - リージョンで99.9%
  - 読み取り、変更を四半期に1度程度のデータを保管するのに適している
- Archive Storage
  - ARCHIVE
  - 最小保存期間　365日
  - リージョンで99.9%
  - 読み取り、変更を1年に1回未満のようなデータを保管するのに適している

### アクセス料金
Standard Storage < Nearline Storage < Coldline Storage < Archive Storage
### 可用性
Standard Storage > Nearline Storage = Coldline Storage >= Archive Storage
### データ保管料金
Standard Storage > Nearline Storage > Coldline Storage > Archive Storage
