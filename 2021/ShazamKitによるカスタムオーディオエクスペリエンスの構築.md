# カスタムカタログの活用

- SignatureGeneratorを利用すると、オーディオバッファを「参照」シグニチャーに変換できる
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/362b838e-756a-4d67-b0e5-5b661da35259">
- shazamsignatureファイル形式を用いると、カタログにシグネチャーを追加することができる
  - これはデバイス間で共有できる
- <img width="639" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/48d4b35a-7f1b-4e76-9fa9-b2baf42f7e84">
- Info.plistの設定
  - <img width="638" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/2c18837c-6690-48fe-ab35-b0eb4f1806f5">
- マッチング
  - <img width="640" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/6c5fec72-f052-4d3e-9b11-def0481d8ca4">
  - <img width="636" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/f6e2bb30-6a1c-4c54-8343-cc0e672c658e">
- デリゲートのハンドリング
  - 取得したメディア情報のoffsetを参照して、対象となるoffsetをプロパティにもつインスタンスを特定している
  - <img width="638" alt="image" src="https://github.com/chocoyama/WWDC2021/assets/7239831/bc756661-4034-418e-a446-9d0814155065">

＃ Best practices

- `.shazamcatalog` はデバイス間でシームレスに共有できる
- fileURLでディスクからロード・保存することができ、ネットワークを介した配信も可能
- カタログはAppのローカルに構築するので、参照シグネチャーは事前に取得した上でAppが動作する設計にしておくのが良い
  - ※ カスタムカタログオブジェクトとしてaddしておく
