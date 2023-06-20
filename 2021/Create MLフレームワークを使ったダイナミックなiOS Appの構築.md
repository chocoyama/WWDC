# Training with Create ML

- Create MLはデバイス上で使えるので、斬新で動的なあらゆることがAppで行えるようになる
- つまり、デバイス上でモデルを作成するプログラム用APIに、Appから直接アクセスできる
- ユーザーから学習し ユーザーに適応する能力がAppにもたらされる
- プライバシーも守られる
- <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/84558bc5-7224-46c2-8cb5-560f271efced">
- macOSで使えるもの
  - <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0ba66439-bfdc-4cde-8a03-41a326857cfc">
- iOSで使えるもの
  - <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2bb9beaa-fdd0-42ab-b3ad-55f3a2d9977e">

# Sample

- <img width="612" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/af5419f2-6137-4991-9e01-9d571f867de5">
- <img width="610" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dd0d8893-cbea-4bd9-ad6d-c8c999ce1390">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/18d31dcc-df3a-4e32-a693-e8f12d94de25">
- <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/71d27b5b-30c0-4e5b-bd91-e0d5a90a35cf">
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a33dacc8-977e-4987-9a72-89825295f7ed">
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d5acb2f0-2bb6-4569-ac60-27f120492251">
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8d469dac-7ed4-4b51-9a28-6a241a29b737">

# 構造化された表形式データの分類や回帰

- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/972e936d-2407-498c-b13d-79b6a7a5d98f">
- 分類はトレーニングデータセットのデータから、特定のクラスを予測することを学習する
- 回帰も同様だが、個別のクラスラベルではなく、数値の予測を学習する
- <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b4385925-eefc-446a-9cb1-6ff18aa3fd3a">
- Appがユーザーの行動を学習し、気に入りそうなコンテンツやおすすめを インテリジェントに出せるようになると便利
  - これは、アプリで表形式の回帰器をトレーニングすることで、実現可能になる
- <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f0f69b9f-e4ce-4ba6-a4dc-93621a13a3c0">
  - コンテンツとコンテキスト、過去のユーザーとのインタラクションを組み合わせることで、今後のインタラクションを予測できる
- 回帰器をAppに追加するには3つのステップがある
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9800b7e3-3697-46aa-b80a-d4aa6d891bf2">
- Prepare Data
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/16478b36-4433-4cd6-b66e-ab9fb92ab2cd">
  - <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8a5d2375-c866-47ff-8947-f548b9412262">
  - 生成した特徴量と正の目標値をエントリとして追加する
  - Negativeな設定を入れるために、関連しないキーワードも合わせて負の目標値をセットしておくことで、制度が高まる
- Train model
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3d337efd-cfc8-4a72-921a-287118d55bab">
- Make prediction
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e8cdd314-bbc1-445d-9b0a-e30865a34138">

# Best practices

- <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/c6d8caad-daf8-4927-800c-7f35e7201087">



