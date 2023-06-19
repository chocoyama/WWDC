# Widget

- Intentの設定がコードで行えるようになった
  - <img width="617" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/6a5cf9ef-afbc-4c34-952b-3fec126dba76">
  - <img width="612" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/19cda0fe-8604-4839-908f-9bcabc8f966a">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/cee12ddf-bfbd-478e-8584-d258142119d9">
  - <img width="608" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/8697a341-1286-4a22-baf3-b7cd6b42afb0">
- ちなみに以前はこんな感じで定義していた
  - <img width="632" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/4cad1dd3-34af-4911-8d97-474e4b7139d6">
- 旧定義からのコンバートも1クリックで行える
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/493a5b1c-76ae-4bae-9bd1-8560ef26e0fe">
- Widget用に作成したIntentはそのままShortcutにも流用できる
  - Widgetのインタラクションに用意したIntentも、ShortcutのActionとして使える

# Dynamic options

- <img width="612" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/a486bb20-f9a6-4818-8b31-a95b38d141ce">
- DynamicOptionsProviderまたはQuery内のIntentからパラメータにアクセスするためのプロパティラッパーである `IntentParameterDependency` がiOS17で追加
- `ShowNextBus`AppIntentの `busStop` パラメータが指定されている場合のみ値を返却している例
  - <img width="616" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/681cade0-88d7-453d-ad5a-cc4182194805">
- 複数指定も可
  - <img width="617" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/f63fa6c4-5e2b-451d-80a1-6d05c5bcbb42">
- Arrayのサイズ指定が可能になった
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/7b4622b2-1029-4e81-ac87-363ea81c635f">
- `ParameterSummary` を使うと、どのパラメータをどのような条件で表示するかを定義することができる
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/1365c644-6556-4846-b451-44725e35e17e">
- 条件を指定することも可能
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/9c1b1ab9-89fe-4bc5-be38-ecddb5d1f658">

# UserActivity

- WidgetをタップしてAppが起動した時の引き継ぎ処理
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/afa1338c-e5a4-434d-927f-61551a692b59">
- RelevantContext APIを使えば、このIntentとその関連する日付範囲を指定することができる
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/d9361516-32f7-4c56-8b65-372de0df9470">
  - 関連する日付情報を提供することで、ウィジェットは自動的にスマートスタック内で提案され、最も重要なときにアクセスできるようになる

# AppIntentsPackage

- Framework化することが可能に
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/50e339fc-468c-4dae-a721-92f173eceed2">

# ForegroundContinuableIntent

- 最初はバックグラウンドで作業を開始するが、フォアグラウンドでの継続を要求する必要があるかもしれない Intent のために設計されたプロトコル
  - ネットワークなどの問題などによって失敗した場合に、Appを起動して続きの作業を行うなどのユースケースに用いることができる
- <img width="620" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/80af3091-3a30-4485-8b49-97aac483355b">
- <img width="610" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/3fdcb098-7b0f-4189-a452-2bec75c8b467">
- <img width="626" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/5f7e0d72-bfef-4151-9a9f-8199b2d88cbc">

# ApplePay

- AppIntentで使えるように
  - <img width="632" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/5dc8cf5e-7fb8-4164-afbc-0de10e9b6c0d">

# Shortcut

- <img width="619" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/f95981eb-3433-4881-95d8-5fc5f2e424a9">
- ParameterSummaryを指定することで伝わりやすいショートカットになる
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/c8841628-0bcb-448e-ad56-f50b526e71bd">
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/ccfc24a9-5191-4ed5-81ef-c892e93da451">
- `isDiscoverable` をfalseにすることで、ショートカットとしては実行できないようにできる
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/3057c12d-e191-4c95-89f4-63dff6c05e93">
- 進捗状況を伝えることが可能になった
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/a0c81c0d-5c96-4b76-b3de-e8c1b4cb0cd7">
- `EntityPropertyQuery` だけでなく `EnumerableEntityQuery Protocol` で検索アクションに対応することが可能になった
  - <img width="612" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/358e3716-aeda-40f5-a683-7460f8e782b1">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/41620589-98db-4ae9-8faf-826acf86a909">
