- インタラクションとアニメーションが付与できるようになった

# Animations

- 最新のSDKでウィジェットを再コンパイルすると、ウィジェットのコンテンツが変わるたびに、システムはデフォルトのアニメーションでエントリーの間の遷移をアニメーション化する
- OSがTimeline間の差分を見て、よしなにアニメーションを付与してくれる
  - 実装は通常のアプリと同様（デモではidとか振ってた）
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/cb56f097-b990-49ee-8542-507e810a0fd0">
- Xcode Previewsで確認が可能
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/09d6b201-aa72-4be7-98ed-74490458ed5a">

# interactivity

- ウィジェットが表示されているとき、コードは実行されていない
- ウィジェットのタイムラインエントリーを更新することで、ウィジェットのコンテンツに変更を加えることができ、これはインタラクティブウィジェットにも当てはまる
- システム制御のリロードはベストエフォート方式だが、インタラクションによるリロードは確実に実行される
- ButtonやToggleなどを利用してインタラクティブにできる
  - ただし、ウィジェットは別プロセスで動作するので、クロージャの実行やBindingの変更はできない
- Widgetでは、AppIntentsを活用する
  - <img width="613" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/9a354058-92b3-42d6-b13e-8c034e0099b6">
- 詳細については以下を参照
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/c0470a7b-07fd-4fb1-a720-2856d5a7ad0a">
- 対応するIFが追加されている
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/b06730fd-9707-401c-afc6-f06a4f323bec">

#### 実装パス

- AppIntentを定義
  - <img width="655" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/d752aa31-fce8-48ae-8286-01666186a382">
  - perfomメソッドの実行が完了次第、システムがウィジェットをリロードする
  - 若干の遅延が発生する可能性があ流ので、新しく追加された `invalidatableContent` Modifierを使ってアップデートが走るまでViewを無効化することで体験を良くできる
