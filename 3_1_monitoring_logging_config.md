# Cloud Loggingエージェントの構成

### デフォルト構成
Loggingエージェント`google-fluentd`は`fluentd`にログデータコレクタに変更を加えたもの。  
- [柔軟なログ収集を可能にする「fluentd」入門
](https://knowledge.sakura.ad.jp/1336/)  

デフォルトの構成ではLoggingはデフォルトのログのリストにあるログをCloud Loggingにストリーミングする。  
- [デフォルトのLoggingエージェントのログ](https://cloud.google.com/logging/docs/agent/default-logs?hl=ja)

追加のログをストリーミングするようにカスタマイズもできる。  

![How the Loggin Agent works](https://cloud.google.com/logging/docs/images/logging-agent-operation.png?hl=ja)

