# ShazamKitとは

- <img width="615" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/f81fe2b5-5cf0-4a4e-9ad2-fd14856b1733">

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

- <img width="620" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/21534fd5-5b88-4f58-b8f9-cf4ee14947b9">
- Shazamは音源自体とはマッチングせず、シグネチャーと呼ぶ有損失表現を作り、それとマッチングをする
  - <img width="614" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/e4aa08c0-eb4d-4520-92e5-00e1d1384252">
  - シグネチャーを使うとデータ量をとても小さくできる
  - 可逆不能なのでプライバシー面でも安全になっている

# Catalog

- シグネチャーをまとめたもので、メタデータも含む
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/edf5d618-6898-4aa0-9380-ead8184458f2">
- 自分でカスタムのカタログを作ることもできる
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/a2774d48-1303-4b9a-a5e4-8c3dfb3ab6e6">
- 音源は音楽でなくても良い
  - メタデータの付与も可能で、アプリ内に保存される
- <img width="621" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/daf35fdb-252f-4d1a-a89a-6009fbea3586">

# 実装

- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/e2729256-9fdf-4507-bd68-751800dd15a0">
  - マイクなどの断続的でない音源とのマッチングは、`matchStreamingBuffer`を使う
- <img width="622" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/0b2f33c9-f26e-462f-9c50-4b8618a590dd">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/3c5e8d66-2b86-4a22-a531-81c994de50b9">
