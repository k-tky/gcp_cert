# コマンドライン インターフェース（CLI）

## gcloud CLIとは

Google Cloudリソースを作成、管理するためのCLIツール
- Google CloudリソースとはCloudSLQやCompute EngineなどGoogle Cloudのサービス

gcloud CLIはGoogle Cloud SDKの一部。事前にGoogle Cloud SKDをインストール、初期化しておく必要がある
- Google Cloud SDKにはデフォルトで `gcloud`,`gsutil`, `bq`コマンドラインツールが含まれる。
- 追加のコンポーネントをインストールするには`gcloud comopnents install`コマンドを使用するか、`deb`または`RPM`パッケージをインストールする。


- cloud sdkにはPythonが必要
  - 推奨バージョンは3.5〜3.7、もしくは2.7.9以降

## ハンズオンのためにDokcerを使う

```
docker pull google/cloud-sdk
docker run -td --rm --name container_sdk google/cloud-sdk
docker exec -it container_sdk /bin/bash
```

## SDKの初期化

### ローカルセッションのinit

- initを実行し、各種設定を行う
```
gcloud init
```

- 以下質問があるのでYを入力し、表示されるURLを展開、認証する
```
ou must log in to continue. Would you like to log in (Y/n)? Y

ttps://accounts.google.com/o/oauth2/auth?client_id=XXXXX...
```

- ブラウザにメッセージが表示されたらGoogleユーザーアカウントでログインし、[Google Cloud SDK が Google アカウントへのアクセスをリクエストしています]を[許可]をクリックしてリソースにアクセスする権限を付与

- コードをコピーして認証をする。
```
Enter verification code: 
You are logged in as: [XXX].
```

- デフォルトプロジェクトを選択する
```
Pick cloud project to use: 
 [1] XXX
 [2] XXX
 [3] XXX
 [4] XXX
Please enter numeric choice or text value (must exactly match list item):
Your current project has been set to: [選択したプロジェクト]
```

- Compute Engineのリージョンの選択
```
Do you want to configure a default Compute Region and Zone? (Y/n)?

Which Google Compute Engine zone would you like to use as project 
default?
If you do not specify a zone via a command line flag while working 
with Compute Engine resources, the default is assumed.
 [1] us-east1-b
 [2] us-east1-c
 ・・・
Did not print [24] options.
Too many options [74]. Enter "list" at prompt to print choices fully.
Please enter numeric choice or text value (must exactly match list item):
```
ローカルセッションでの初期化処理

### リモートセッションでの初期化処理
- --console-onlyフラグを利用してブラウザベースの承認フローが開始されないようにできる  
→できなかった。。。
```
gcloud init --console-only
Welcome! This command will take you through the configuration of gcloud.

Your current configuration has been set to: [default]

You can skip diagnostics next time by using the following flag:
  gcloud init --skip-diagnostics

Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.                                                                                                                                                                                                                                       
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

You must log in to continue. Would you like to log in (Y/n)?  
Go to the following link in your browser:

    https://accounts.google.com/o/oauth2/auth?client_id=XXX

```

### その他のコマンドでの実行
- 構成を設定せずにユーザーアカウントを使用して承認を行う
```
gcloud auth login
```

- サービスアカウントを使用して承認（サービスアカウントキーを利用）
```
gcloud auth activate-service-account
```

- Cloud SDKの構成、プロパティの設定
```
gcloud config [COMMAND]
gcloud config configurations [COMMAND]
```