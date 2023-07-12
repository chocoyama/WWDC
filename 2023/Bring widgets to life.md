- インタラクションとアニメーションが付与できるようになった

# Animations

- 最新のSDKでウィジェットを再コンパイルすると、ウィジェットのコンテンツが変わるたびに、システムはデフォルトのアニメーションでエントリーの間の遷移をアニメーション化する
- OSがTimeline間の差分を見て、よしなにアニメーションを付与してくれる
  - 実装は通常のアプリと同様（デモではidとか振ってた）
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/13d5d807-9ecd-4fd5-beed-95565a0c5547">
- Xcode Previewsで確認が可能
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1d2b98e6-ce77-4f10-a3c0-df5342924c7c">

# interactivity

- ウィジェットが表示されているとき、コードは実行されていない
- ウィジェットのタイムラインエントリーを更新することで、ウィジェットのコンテンツに変更を加えることができ、これはインタラクティブウィジェットにも当てはまる
- システム制御のリロードはベストエフォート方式だが、インタラクションによるリロードは確実に実行される
- ButtonやToggleなどを利用してインタラクティブにできる
  - ただし、ウィジェットは別プロセスで動作するので、クロージャの実行やBindingの変更はできない
- Widgetでは、AppIntentsを活用する
  - <img width="613" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/7eec0fd3-d88e-423d-a9bd-5afe458d7f23">
- 詳細については以下を参照
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1d2f0b22-f682-4620-83ff-35d13b866347">
- 対応するIFが追加されている
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2aa60564-911e-41b7-9b70-568316254e39">

#### 実装パス

- AppIntentを定義
  - <img width="655" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d30af155-f9c3-43c0-b1f2-e7a3249b138b">
  - perfomメソッドの実行が完了次第、システムがウィジェットをリロードする
  - 若干の遅延が発生する可能性があ流ので、新しく追加された `invalidatableContent` Modifierを使ってアップデートが走るまでViewを無効化することで体験を良くできる
