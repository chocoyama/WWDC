# Widget

- Intentの設定がコードで行えるようになった
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/ea501588-8832-46fc-8796-d14be1f73cc1">
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/ff12a983-fb84-4115-ac48-bc14e8e0c909">
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/8476daf1-3895-4caf-95ba-5acf5dafa0b7">
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/954a0a67-44fa-4191-85e3-141b266f850f">
- ちなみに以前はこんな感じで定義していた
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/1b11da93-f232-4146-a7a7-fe3233049366">
- 旧定義からのコンバートも1クリックで行える
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/20038a50-f2c6-4eba-b7ee-4a322fbb6115">
- Widget用に作成したIntentはそのままShortcutにも流用できる
  - Widgetのインタラクションに用意したIntentも、ShortcutのActionとして使える

# Dynamic options

- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/880895a1-b160-4cf9-b0db-a12ec9e7e5a9">
- DynamicOptionsProviderまたはQuery内のIntentからパラメータにアクセスするためのプロパティラッパーである `IntentParameterDependency` がiOS17で追加
- `ShowNextBus`AppIntentの `busStop` パラメータが指定されている場合のみ値を返却している例
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/3c000d78-8dc1-4f0c-a315-20132c3c91b9">
- 複数指定も可
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/9529ae9a-6b7d-4c05-a771-482c6d283592">
- Arrayのサイズ指定が可能になった
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/a549c7c4-2d74-4101-ae1e-fb74cd4b0244">
- `ParameterSummary` を使うと、どのパラメータをどのような条件で表示するかを定義することができる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/f1d4f445-ff85-406c-be16-6224c4a8fa2b">
- 条件を指定することも可能
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/a204c03c-8224-42d1-91aa-ea985db5401d">

# UserActivity

- WidgetをタップしてAppが起動した時の引き継ぎ処理
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/5008441f-c911-4c96-94fb-aad54984d251">
- RelevantContext APIを使えば、このIntentとその関連する日付範囲を指定することができる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/45e21589-99d0-4209-bed1-857d20be682c">
  - 関連する日付情報を提供することで、ウィジェットは自動的にスマートスタック内で提案され、最も重要なときにアクセスできるようになる

# AppIntentsPackage

- Framework化することが可能に
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/d9a634b4-fa49-4a87-8aef-8da978bb9874">

# ForegroundContinuableIntent

- 最初はバックグラウンドで作業を開始するが、フォアグラウンドでの継続を要求する必要があるかもしれない Intent のために設計されたプロトコル
  - ネットワークなどの問題などによって失敗した場合に、Appを起動して続きの作業を行うなどのユースケースに用いることができる
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/0ec8cc5a-ebbd-45a2-9945-50b495b9d063">
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/5580614a-a284-43bb-91e5-89ac6d1e27dd">
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/de591c71-dee7-474f-8a32-a5747de661c9">

# ApplePay

- AppIntentで使えるように
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/45767569-5b25-4f2d-85c0-202e48d790fe">

# Shortcut

- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/cb5619ac-8a4f-4c63-a7c8-543961416bf1">
- ParameterSummaryを指定することで伝わりやすいショートカットになる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/014e5464-540d-4387-80e8-0a1dd4d6a8b7">
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/cc64faca-bcde-4593-a9d9-ddeea0c3826b">
- `isDiscoverable` をfalseにすることで、ショートカットとしては実行できないようにできる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/29683507-12f5-43b3-ac98-5945d506ad43">
- 進捗状況を伝えることが可能になった
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/0efaabbf-ec32-480f-baaf-7797e37303a0">
- `EntityPropertyQuery` だけでなく `EnumerableEntityQuery Protocol` で検索アクションに対応することが可能になった
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/61fd054b-badc-4d1a-814d-66687f5d562f">
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/36da6d73-edb1-416a-8626-508351071f80">
