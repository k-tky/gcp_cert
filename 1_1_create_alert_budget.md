# [予算と予算アラートの設定]((https://cloud.google.com/billing/docs/how-to/budgets?hl=ja))
予算を作成して、Google Cloudの課金を管理することで課金状況の管理ができる。  
予算が閾値を超える時に予算アラートの通知（メール通知）を設定することができる。  

予算アラートのデフォルト動作
![図1](https://cloud.google.com/billing/docs/images/budget-alert-diagram-all.png?hl=ja)

- Cloud Billing予算の場合

1. 予算の範囲を定義できる。Cloud請求先アカウント全体の予算や個別のプロジェクトの予算の定義ができる
2. 予算額の指定方法は指定額、もしくは前月の利用額に基づいて設定ができる
3. 設定した予算を超えると、対象となるCloud請求先アカウントの`請求先アカウント管理者`、`請求先アカウントユーザー`にアラートメールが送信される
4. Cloud Monitoringを利用してメール受信者をカスタマイズし、組織内の他のユーザーにメール通知ができる
5. Pub/Subによる通知ができる