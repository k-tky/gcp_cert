# Stackdriver(Cloud Monitoring) ワークスペースをプロビジョニングする

### ワークスペース
1つ以上のGCPプロジェクトやAWSアカウントに含まれるリソースをモニタリングするためのツール。  
ワークスペースを通じて指標データにアクセスする。
Cloud Monitoringではワークスペースを利用してGCPリソース（AWSも利用可）のモニタリング情報を表示する。

### ホストプロジェクト
ワークスペースの作成に使用されるGCPプロジェクト。  
ワークスペースの名前はホストプロジェクトの名前に設定される。
ワークスペースに構成されたダッシュボード、アラートポリシー、稼働時間チェック、通知チャネル、グループ定義はホストプロジェクトに保存される。
ホストプロジェクトを削除するとワークスペースも削除される

![イメージ図](https://cloud.google.com/monitoring/images/Workspaces-1.0c.png?hl=ja)

### モニタリング対象プロジェクト
一つのワークスペースには最大100個のGCPプロジェクト、AWSアカウントをモニタリングするように設定できる。  

![イメージ図](https://cloud.google.com/monitoring/images/Workspaces-1.0b.png?hl=ja)

### AWSコネクタプロジェクト
AWSアカウントをモニタリング対象に追加すると、モニタリングによってAWSコネクタプロジェクトが作成される。  
コネクタプロジェクトには`AWS Link`から始まる名前がつき、ワークスペースと同じ組織に所属する。

### 課金
ワークスペースの作成に対しては課金は発生しない。  
指標データやロギングに対する課金は発生したプロジェクトの請求先アカウントに行われる。  
AWSアカウントの場合はAWSコネクタプロジェクトの請求先アカウントに課金が発生する。

### Monitoringの停止
モニタリングを停止するにはAPIを無効化する。  
1. Consoleから「APIとサービス」へ移動する
2. 「Stackdriver Monitoring API」を選択する
3. APIを無効化する