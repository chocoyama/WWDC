# SHManagedSession

- 録音とマッチングを簡単にするための新しいAPI
- オーディオバッファを設定する手間をかけずに、自動的に録音開始を代行する
- マイクのUsage descriptionをInfo.plistに定義
- Single Match
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/32532788-bdb9-41e9-9f1d-04808c2c0b67">
- Continuous Match
  - <img width="633" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/ac9bdd16-25d6-442f-a2af-29be1cb0f9e7">
- キャンセル
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/70514051-d5cf-49d3-bff8-2bd5ee7b4625">
- トラッキングのBefore/After
  - <img width="634" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b8c73a5b-aba3-4b5a-affc-057ea24e9c0b">
  - <img width="636" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/7ac78b06-64be-4964-b25d-533f9bd148b8">
- キャンセルのBefore/After
  - <img width="637" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8a2a1386-ff1d-4eb4-a862-3d6d0a17e269">
  - <img width="638" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/4fb8299a-2c4f-435f-b976-e950256b9cab">
- prepareメソッドの活用によるパフォーマンスの向上
  - prepareを利用しない場合
    - <img width="634" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/bf7de70b-ab85-47b0-a5e6-19c84dec1527">
  - prepareを利用する場合
    - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/21ab1bbd-235a-4209-a416-753e1a9577d7">
- Stateの取得が可能
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/eb76eeb6-6ff9-4bce-b7f2-110d60c39602">
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/973ca002-6613-42a6-b772-2d45c47e8750">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/07017bb6-bbd3-4bdb-83e1-2c108c7b083e">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f0ab73b4-6128-41cd-98e8-10e55adf23ba">
  - Observableに準拠しているので、UIへの状態反映もしやすい
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6f81681a-1d19-48c7-ae67-b9afc9e0fa99">

# SHLibrary

- 自身のアプリで取り扱ったShazamItemを、ローカルDBで管理できるみたいなイメージ
- 端末間でのリアルタイム同期もサポート

# Custom catalogs

- カスタムカタログに類似した音声が2ビット以上ある場合、複数の参照シグネチャに一致するクエリーシグネチャを渡すと、カスタムカタログからすべてのマッチを返すことができるようになった
  - マッチは最高のマッチ品質でソートされて返され、適切なマッチ結果をフィルタリングすることができる
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/c2a95fb0-7fd1-4f9f-92fd-0767290da517">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5d35f2e0-3628-4287-9719-ca4bf92e49ff">

