# ShazamKitとは

- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/f17b8505-dded-40b8-a25c-dcb2c253c535"/>

# カタログ探知

- Shazamのカタログ照合ができる
- 音の演出する雰囲気も取れる
- ジャンルなどのメタデータなども取得可能

# 音声探知

- 音声を探知して特定のアクションをフックすることができる
- ex
  - 合言葉を発話すると何かのアクションが実行される
  - テレビで商品名が発話されるたびに検索を実行してAppに表示する

# 仕組み

- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/5885c1e9-8b96-40cc-b5fb-d7acf41f0626"/>
- Shazamは音源自体とはマッチングせず、シグネチャーと呼ぶ有損失表現を作り、それとマッチングをする
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/5edc07f8-bb6a-4595-a5f5-e08883c1ce4c"/>
  - シグネチャーを使うとデータ量をとても小さくできる
  - 可逆不能なのでプライバシー面でも安全になっている

# Catalog

- シグネチャーをまとめたもので、メタデータも含む
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/d0b90dfe-4c5e-4307-b027-da80a1ad8dc5"/>
- 自分でカスタムのカタログを作ることもできる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/42665d93-1502-4747-b266-a299c79e8157"/>
- 音源は音楽でなくても良い
  - メタデータの付与も可能で、アプリ内に保存される
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/6afe1531-8d41-4931-9e9e-691ece3620d3"/>

# 実装

- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/881ea296-f2f9-47a1-8cc7-4416f02daf52"/>
  - マイクなどの断続的でない音源とのマッチングは、`matchStreamingBuffer`を使う
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/fc94d698-0659-4124-b9aa-baed1628e208"/>
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/0bbb04cd-5ed5-4eee-b871-c1ebd5c7deb5"/>
