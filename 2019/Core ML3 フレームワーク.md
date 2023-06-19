# Personalize

- <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9c453cd6-34ef-467b-8e5d-879369bc121e">
- 標準的なモデルとユーザーによって生まれたデータを組み合わせてパーソナライズができる
- モデル内部
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/036732a9-636d-4e74-a270-6c60181f7970">
  - Core ML3でパラメータが増えた
    - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b570d42a-6589-4d2a-be66-1e9094d4a099">
- Core ML3では分類子やニューラルネットワークのモデルのアップデートが可能

## Demo

- ユーザーに事前にショートカットとなる絵を登録してもらい、以降はそれに類似した絵がインプットされたら推論できるようにしている
  - <img width="632" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dd9cc760-4cce-454d-9a59-1d779640166c">
  - <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5b1f3b9c-2970-480f-b010-2ef5e2c0b3fd">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3111955b-a36e-4654-b9a0-bec74e656d53">
- 必要な対応
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9f376844-70c7-4550-8948-049278193f8c">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/162de60e-3f0b-481f-96e9-ba1cf15ab287">
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/c8ef03c4-eea4-41d2-9e8f-9898627096c7">
  - <img width="635" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/93e40bfe-34f5-4949-a939-d306fc487989">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e24fa9c6-eb24-452f-8248-732952628d4e">

## 高度なパーソナライズ

- <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dfc511c4-a73d-4424-8161-130cbc9832f8">
- <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3b391cb3-5ef2-476e-ae02-7437dc00ae47">
- <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8dc04250-bece-4d42-b7a3-2af55f2d9ddc">
- <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/47ca215b-f433-40f5-9628-ef6d5a42b215">
- ニューラルネットワークの場合
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/075fe7ca-2b1f-4c74-8a5e-ccbb0db2f229">
  - アウトプットを調整するには レイヤの重みを調整する必要がある
  - そのために、レイヤをアップデート可能にする
  - オプティマイザが正解でないアウトプットを正確に導くための調整を行う
    - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1384b5b1-799f-40ae-9b57-3193a02df2c4">
    - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a4782757-7b25-4c2e-b8b1-4cbb7648299f">
- ランタイムを変更したい場合は
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/853e95a4-fa4f-4db9-b61f-d79a3d3bff08">
- さらに柔軟性を求めたい場合は
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b8b2dacb-ab57-4aee-857d-01a70d60ad46">
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d0aaffef-1ce1-4163-a4dd-6321d84d17a7">

## Background Update

- 大量のデータがある場合はフォアグラウンドでUpdateしない方がいい場合もある
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/629015e7-6228-44f2-82bc-d909ec517373">

# Neural Networks

- ニューラルネットワークはタスク解決に適している
- 画像やドキュメント、音声の内容を理解しようとする

# その他アップデート

- <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/306b81d5-fe87-443b-aa12-ca3559e02b1a">
