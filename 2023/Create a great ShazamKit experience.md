# SHManagedSession

- 録音とマッチングを簡単にするための新しいAPI
- オーディオバッファを設定する手間をかけずに、自動的に録音開始を代行する
- マイクのUsage descriptionをInfo.plistに定義
- Single Match
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/63094d51-a49a-440b-a873-a720be24b0fc">
- Continuous Match
  - <img width="633" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/4a9bc34e-724a-4955-974a-4a63e93027e9">
- キャンセル
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/9a196ba5-ad86-4c0f-8866-e57f872d0045">
- トラッキングのBefore/After
  - <img width="634" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/517311c5-d8ed-49b5-b7bd-742f4b6bed67">
  - <img width="636" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/394bebd8-fd97-411a-897e-e5e195c81f47">
- キャンセルのBefore/After
  - <img width="637" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/2ac59032-eb3d-4bb9-b63c-77e820800f6e">
  - <img width="638" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/8f2cbf24-78aa-4690-aa78-de5c351b08bd">
- prepareメソッドの活用によるパフォーマンスの向上
  - prepareを利用しない場合
    - <img width="634" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/d1d12268-fb0a-42be-b926-e93d48ad2dae">
  - prepareを利用する場合
    - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/bbfd20e0-f95f-46bf-87d4-7960a403ae2e">
- Stateの取得が可能
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/6b7ee0a3-64d8-449b-b651-7f2e9f4f5e84">
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/a3db62f9-4c97-48ff-809a-785e964caf9d">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/743cdf3f-6d12-4364-b4aa-75ea14a30f0e">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/97e958ba-7bba-475c-baa7-2dc0805ac08e">
  - Observableに準拠しているので、UIへの状態反映もしやすい
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/2a62ece7-be47-4cb9-a98d-668c7e707f19">

# SHLibrary

- 自身のアプリで取り扱ったShazamItemを、ローカルDBで管理できるみたいなイメージ
- 端末間でのリアルタイム同期もサポート

# Custom catalogs

- カスタムカタログに類似した音声が2ビット以上ある場合、複数の参照シグネチャに一致するクエリーシグネチャを渡すと、カスタムカタログからすべてのマッチを返すことができるようになった
  - マッチは最高のマッチ品質でソートされて返され、適切なマッチ結果をフィルタリングすることができる
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/677680fb-f201-4e11-b0b0-45623ff6df2c">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/76f6a7dc-c84f-4a4c-89ab-ef2e561e19a4">

