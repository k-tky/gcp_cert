# マネージドインスタンスグループ（MIG）
MIGとは共通のインスタンステンプレートから作成されるVMのコレクション。  
Compute Engineにはマネージド、非マネージドがあるが、オートスケーリング機能を持つのはマネージド。  
負荷の増減に対してMIGからVMインスタンスを自動で追加、削除が行われるオートスケーリング機能を備える。  
オートスケールのためのポリシーを定義できる。

- オートスケーリングはゾーンとリージョンのMIGで機能する。非MIGは機能しない
- プロアクティブなインスタンスの再分配が無効になっている場合はリージョンMIGはオートスケーリングが機能しない
- オートスケーリングはステートフルMIGでは機能しない
- オートスケールでは特定（指定）のインスタンス名は設定できない。
- MIGにステートフル構成がある場合はオートスケーリングは機能しない
- GKEに所有されるMIGは自動スケーリングを使用しないようにする。
- オートスケーラは複数の指標に基づいてスケーリングを決定できるが、指標タイプごとに1つのポリシーのみ設定できる。
- オートスケーリングとセルフヒールは別個の動作をする。セルフヒールの結果、オートスケーリングの閾値を下回ることはある。
- リージョンMIGをオートスケーリングするとインスタンスが追加されたのちにすぐにいずれかのゾーンからインスタンスが削除される場合がある

### オートスケーリングの目標値、ポリシー
オートスケーラがスケーリングの判断をするために設定する値
- 平均CPU使用率
- 使用率、または1秒あたりのリクエスト数のいずれかに基づいたHTTP負荷分散処理能力
- Cloud Monitoringの指標

### クールダウン期間
VMインスタンスの初期化中は使用状況が通常の状態と乖離しているため、正しくモニタリングがされていると判断できないためクールダウン期間が設けられる。  
デフォルトでのクールダウン期間は60秒

### 安定化期間
オートスケーラがスケールインのために計測している直近10分間のVMインスタンスの各種状態のこと。  
この10分間のことを安定化期間と表現する。

### オートスケーリングモード
一時的にオートスケーリングを無効化、または制限ができる。