# Cloud データベースの選択
各プロダクトの選択

### CloudSQL
クラウド上のフルマネージドのRDB。MySQL、Postgre、SQL Server
- 推奨用途
  - WordPress
  - バックエンドのDB
- 比較対象
  - AWS RDS
  - Azure Database

### Cloud Bigtable
低レイテンシ、高スケーラブルなNoSQLなデータストア
- 推奨用途
  - 大規模な分析ワークロード
  - 低レイテンシなアプリケーション（IoT、センサーなど）
- 比較対象
  - HBase
  - Cassandra
  - AWS DynamoDB
  - Azure CosmosDB

### Cloud Spanner
リージョン、地理的なロケールをまたがって強トランザクション、強整合性、高可用性を持つSQLインターフェースを持つDB  
（実態はNoSQL）
- 推奨用途
  - スケール保証が必要
  - ミッションクリティカルな可用性を求めるシステム
- 比較対象
  - AWS Aurora

### Cloud Firestore
フルマネージドのNoSQLドキュメントDB
- 推奨用途
  - クライアント側モバイルWebアプリケーション
  - ゲームリーダーボード
  - グローバル規模のユーザープレゼンス
- 比較対象
  - AWS DynamoDB
  - MongoDB
  - Azure CosmosDB

### BigQuery
PB単位のデータ解析を行えるフルマネージドなDWH
- 推奨用途
  - リアルタイム解析
  - 予測分析（BQML）
  - エンタープライズ
- 比較対象
  - AWS Redshift
  - snowflake
  - Azure SQL Data Warehouse