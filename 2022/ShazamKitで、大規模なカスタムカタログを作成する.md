# シンプルなカタログの作成

- 以下の対応を行う
  - ShazamKitが使用できる形式でオーディオを録音
  - シグネチャジェネレータを用いて、シグネチャに変換
  - メタデータの付与
  - カスタムカタログに保存

# Shazam CLIで大規模なカタログを作成する

- コンテンツの同期を簡易化する方法を提供する
- カタログ生成関連タスクの自動化をサポートする
- 動画をSignatureに変換
  - <img width="608" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/bfc51fbc-b4c7-429f-9bdc-ec8e3272ad65">
- コンテンツの同期に必要な情報をcsvファイルで用意
  - <img width="640" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/2501a444-2565-4615-baa0-b517ffbe4903">
- helpコマンドで指定可能なプロパティの一覧ができる
  - <img width="458" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/40bd94f1-96fd-463e-9658-40febd289ed4">
  - <img width="636" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/a1db4f22-ae85-4ebc-af36-82c01feb1d72">
- カタログの作成
  - <img width="548" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/c68a67ef-52e8-4922-b298-ded918f31842">
- アップデートする場合
  - <img width="600" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6dd8b2f8-8c55-49a2-9380-ec940d8f3493">  
- 実装の方はこんな感じ
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/1127e1a1-4394-45c3-9535-e4f1f0500086">

# シグネチャの作成

- オーディオトラックを含むあらゆるメディアファイルから作成でき、シグネチャとメディアアイテムを合わせたカスタムカタログを生成できる
- オーディオトラックのついたAVAssetをパスしてシグネチャにできる
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/e8e2b959-4e56-40e5-875c-61f426daaba5">
- 正確なコンテンツの同期には `Timed Media Item API` を活用する
  - メディアアイテムに時間を付与することで開始時間・終了時間の特定が簡単になった
  - <img width="632" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/d36ab28e-d391-4bab-93a7-d35ccbde8bf3">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/807b701d-6213-4353-b26a-ef5e14cd038f">
- 返却されるルール
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/e038a680-982e-4a54-85e7-6ccd43a46509">
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/04a8c397-b832-4100-a58e-1aad75f6ff6c">
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/05099588-1434-4b21-bd30-b8247219cc5b">
- 時間範囲のないんものは、リファレンス全体に適用される全体的な情報を保存するのに適している
  - ex. エピソード名の保存場所（他のメディアアイテムが見えない場合に現れる）

# Tips

- メディア1つに対して複数の小さなシグネチャは作らない
  - <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/bb1c1c0d-911a-4dae-98d4-94aa5da72452">
  - 1つのオーディオに対して、最初から最後までで1つのシグネチャにする
  - シグネチャが長い方が精度が上がる
    - <img width="616" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/5fea3444-eda4-4990-9c51-ff20d4371ab8">
  - Timed Media Item APIを使えば、単一のシグネチャから複数のメディアアイテムを取得して同期することができる
- カタログの追加
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC2022/assets/7239831/26e93a6a-8823-4f4c-a0fd-cfbc57811c50">
