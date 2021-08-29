# 高度な方法によるインスタンスへの接続
自分自身で認証情報を管理する、サードパーティのルールを使用する、または別の接続パスを使用してインスタンスに接続する必要がある場合  
### Linuxインスタンス
- サードパーティツールを使用してインスタンスに接続する
- 外部IPアドレスを持たないインスタンスに接続する
- rootユーザーとしてインスタンスに接続する
- セキュリティキーを使用したSSH
### Windows Serverインスタンス
- PowerShellターミナルを使用してWindowsインスタンスに接続する


### 公開SSH認証鍵をインスタンスに渡す
インスタンスに認証鍵を渡すには以下のいずれかの方法を使用する
- *推奨* OS Loginを有効にする。OS LoginではIAMのロールを使用してGoogleアカウントまたはマネージドユーザーアカウントを通して公開SSH認証鍵をインスタンスに渡す。
- *非推奨* プロジェクトまたはインスタンスのメタデータを編集してSSH認証鍵を手動で追加及び削除を行う。

### OS LoginによるSSH認証鍵の渡し方
opensslを利用して秘密鍵、公開鍵を作成する  
```
# 秘密鍵の作成
openssl genrsa > secret.key
# 秘密鍵から公開鍵の作成
openssl rsa -pubout < secret.key > public.key
# 自分のアカウントの現在のユーザー名を調べる
gcloud compute os-login describe-profile
# 公開鍵の追加（アカウントへの登録）
gcloud compute os-login ssh-keys add --key-file=public.key --ttl=0d
gcloud compute os-login ssh-keys remove --key-file=public.key
```

### SSHキーを登録した後にインスタンスに接続

```
gcloud compute ssh --project PROJECT_ID --zone ZONE VM_NAME
```

デフォルトのアカウントで接続される。  
`user@exsample.com`の場合、`user_exsample_com`のユーザー名で接続される