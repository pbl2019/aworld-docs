# aworld-docs
Aworldの仕様や用語定義など

```
- (Human) Player Character(プレイヤーキャラクター)
  HPC。人間の操作するキャラクター
- Autonomous Player Character(自律プレイヤーキャラクター)
  APC。AIの操作するキャラクター
- Data Server
  ゲーム状態を更新・保持するgRPCサーバ。更新の手段を持つデータベース。
  定期的(10s程度)にMySQLなどで永続化。
  リクエストはキューイングされる。観測リクエストではタイムスタンプを受け取り、それ以降に更新された差分を返す。
- Control Server
  HPC・APCのコントローラーの状態を管理するWebSocketサーバ。
  Clientからボタン操作情報を受け取り、定期的(10〜100ms程度)にData Serverに通知、ゲーム状態を更新させる。
  Data Serverへの通知でレスポンスは受け取らず、ストリーミング方式で通信する。
```
