# VNRecognizeTextRequest

- <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8c2a872d-d562-443d-9723-aa6e0847f5c0">
- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/19e14e51-46fb-4a6c-b6fc-eeab3f7750fd">
- <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/794d3884-f152-4a48-84db-5d985ab705bd">
  - “Fast”は、テキスト認識の経験に基づいて文字を見つける
    - そして機械学習モデルを使って、それぞれの文字を実際に認識する
    - リアルタイムの読み込みに適している
    - メモリの負担が少ない
    - 斜体・筆記体・珍しいスタイルなどは信頼性が低い
    - 自然言語の読解力が低い
  - “Accurate”は、最先端のニューラルネットワークを使用
    - 文字列と行を見いだすことでテキストを検出し、さらに単語や文として認識することができる
    - 必要となるディープラーニングモデルは時間を要するが、読む量は人間を上回る
    - 非同期での利用に向いている
    - メモリの負担が大きい
    - 斜体・筆記体・珍しいスタイルなどにも対応できる
    - 自然言語の読解力が高い
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6acaabcd-0194-4f4b-b75b-7a9ad6294a35">
    - 左が"Fast"で、右が"Accurate"
- 言語処理
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/74418f0f-4227-456f-b267-e330f56d3f0e">
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f1c29a26-1f9c-44fc-9e2c-c316bde18217">
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/21771851-b947-4da1-b9ed-89344218f62b">
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dc62ee9a-ef66-4f0e-8f07-13b10124d5f5">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8a0d3a31-bcfe-4093-aa9e-4eb1a61dd655">
    - 扱うデータが限られて、パフォーマンスが向上する
  - AVCaptureSessionで画像を取得して、リクエストを行う
    - <img width="601" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/200f5789-749e-40d1-b51b-7603f12558bd">

# Document Camera

- 文書の読み取りに使えて、そのままテキスト認識のリクエストが行える
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8ea17c9a-0e19-41d3-aa6b-78ec59c38095">
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/20d99029-0baf-4be4-bae8-cc034285891f">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/fea98d4d-b29a-4e82-93ed-84e746c44d5e">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/860fe0a6-19b4-4316-a28d-af93b4787f71">

# Best Practices For Text Recognization

- カスタム語彙の指定
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/bfef97d6-aa98-4405-83b7-c838d3af20eb">
- minimum text height（画像の高さに対する割合）
  - <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/7342b795-86c7-4a54-817d-26aefb20601c">
- 他のタスクの優先度を上げたい場合、GPUリソースやNeural Engineを利用しないようにもできる
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/987d5a4a-eb78-4d5a-b177-2f4d7b82771b">
- 進捗のFB
  - <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f1aac095-1d77-4629-95a9-2811787b4c73">
- 紛らわしい情報に備える
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/22752fe1-c21a-4796-81fc-4eecf8714ced">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a0ab8de0-4d17-4db5-8f31-22c6cbbf4572">
- Geometryの活用
  - `observation.boundingBox` で空間情報を得ることができる
  - 位置、結果の基準、回転を利用して結果を関連付けることができる
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/30937c89-66a2-4dd1-9189-e71301657220">
- パーサーの利用
  - NSDataDetectorを用いて情報の抽出ができる
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/31bd5e8a-8d3e-49dc-928f-37f31cc7ee8b">
- 最後にドメイン知識を用いる
