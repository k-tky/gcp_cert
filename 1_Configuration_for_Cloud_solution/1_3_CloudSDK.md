## コマンドライン インターフェース（CLI）

- cloud sdkにはPythonが必要
  - 推奨バージョンは3.5〜3.7、もしくは2.7.9以降

### ハンズオンのためにDokcerが使える

```
docker pull google/cloud-sdk
docker run -td --name container_sdk google/cloud-sdk
docker exec -it container_sdk /bin/bash
```

### SDKの初期化

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



