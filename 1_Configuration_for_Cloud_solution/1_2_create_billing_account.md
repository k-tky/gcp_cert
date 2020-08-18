# 請求先アカウントの作成、変更、閉鎖

### 請求先アカウント
Google Cloud プロジェクト、Google Maps Platformプロジェクトの料金が請求されるアカウント。  
各プロジェクトの請求先アカウントは常に一つしか存在しない。  
請求先アカウントは複数のプロジェクトの請求先に設定できる。  


### 請求先アカウントの作成
組織に所属するメンバーの場合、`請求先アカウント作成者`の権限が必要  
- `billing.accounts.create`  

1. Google Cloud Consoleの[請求先アカウントを管理](https://console.cloud.google.com/billing?hl=ja&_ga=2.181374752.688251329.1597712176-1447708693.1572597414)ページに遷移する。
2. ［アカウントを作成］をクリックし、以下を設定して[続行]する
    - 請求先アカウントの名前を入力する
    - [組織]プルダウンが表示された場合は、組織を選択する
    - [国]を選択する必要ばある場合は居住する国を選択する
3. 請求先アカウントに紐づける`Google お支払いプロファイル`を選択する  
※お支払いプロファイルとは支払い者の名称、住所や支払い方法、クレジットカード番号などのプロファイル
    - アカウントの種類について  
    お支払いプロファイルは永続的でアカウントの種類を設定する際には以下を留意する  
    VATなどの各種税金や本人確認に利用される。企業、組織、組合、教育機関の場合は[ビジネス]、それ以外の場合は[個人]を選択する  
    複数のGoogle Cloudプロジェクトの請求先アカウントに設定する場合は[ビジネス]にする必要がある。[個人]のアカウントの場合は一つのGoogle Cloudプロジェクトの請求先アカウントにしかできない。

### メールアドレスの確認
請求に関する通知を受信できるようにメールアドレスを設定する。[メインの連絡先]に指定されたメールアドレスに通知が行われる。  
連絡先の確認は以下の手順で実行する
1. Google Cloud Consoleの[請求先アカウントを管理](https://console.cloud.google.com/billing?hl=ja&_ga=2.187648943.688251329.1597712176-1447708693.1572597414)ページに遷移する
2. 確認するCloud請求先アカウントの名前を選択する
3. [お支払い]ナビゲーションで[お支払い設定]をクリックする
4. [お支払いサービスのユーザー]で確認するメールアドレスを探し、[確認メールを再送信]をクリックする。（すでにメールアドレスが確認されている場合はリンクは非活性になる）

### 請求先アカウントの送付先住所を変更する
送付先住所の変更にはCloud請求先アカウントの[請求先アカウント管理者]である必要がある  
- `billing.accounts.updatePaymentInfo`
1. Google Cloud Consoleの[請求先アカウントを管理](https://console.cloud.google.com/billing?hl=ja&_ga=2.187648943.688251329.1597712176-1447708693.1572597414)ページに遷移する
2. 更新するCloud請求先アカウントを選択する
3. [お支払い]ナビゲーションで[お支払い設定]を選択する
4. [お支払いプロファイル]で名前と住所の横にある編集アイコン（edit）をクリックして送付先住所を編集する
5. 送付先住所を更新し、保存する

### 請求先アカウントを閉鎖する
請求先アカウントの閉鎖にはCloud請求先アカウントの[請求先アカウント管理者]である必要がある
- Cloud請求先アカウントに対する`billing.accounts.close`
    - Cloud請求先アカウントに紐づけられたプロジェクトの有料リソースはCloud請求先アカウントが閉鎖されると全ての有料リソースはサービスを停止する
    - プロジェクトのリソースはアクティブなままにした状態で紐づけられたCloud請求先アカウントを閉鎖する場合は別のCloud請求先アカウントにプロジェクトを紐づけてから閉鎖する
1. Google Cloud Consoleの[請求先アカウントを管理](https://console.cloud.google.com/billing?hl=ja&_ga=2.187648943.688251329.1597712176-1447708693.1572597414)ページに遷移する
2. 閉鎖するCloud請求先アカウントを選択する
3. [お支払い]ナビゲーションで[アカウント管理]を選択する
4. ページ上部にある[請求先アカウントを閉鎖]をクリックする

### 閉鎖された請求先アカウントを再開する
請求先アカウントの閉鎖にはCloud請求先アカウントの[請求先アカウント管理者]である必要がある
- CLoud請求先アカウントに対する`billing.accounts.reopen`
1. Google Cloud Consoleの[請求先アカウントを管理](https://console.cloud.google.com/billing?hl=ja&_ga=2.187648943.688251329.1597712176-1447708693.1572597414)ページに遷移する
2. [有効なアカウントのみを表示]プルダウンをクリックし[すべてのアカウントを表示]を選択する
3. 再開するCloud請求先アカウントを選択する
4. [お支払い]ナビゲーションで[アカウントを管理]をクリックする
5. ページ上部にある[請求先アカウントを再開]をクリックする

### 請求先アカウントの削除
Cloud請求先アカウントの削除はできない。レポートと監査のために、Cloud請求先アカウントは保持される。