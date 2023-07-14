# カスタムカタログの活用

- SignatureGeneratorを利用すると、オーディオバッファを「参照」シグニチャーに変換できる
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/06a5eedd-b946-4e5d-a609-2d5625f2b29c"/>
- shazamsignatureファイル形式を用いると、カタログにシグネチャーを追加することができる
  - これはデバイス間で共有できる
- <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/8fff4ca7-8b2d-44b3-b99c-4eca3ee7209e"/>
- Info.plistの設定
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/f63497fe-c9cc-4571-8dbf-7521667d066c"/>
- マッチング
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/a09b1272-c093-41d6-bf81-8adb8191a165"/>
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/8aa2e375-8cf6-4916-99bb-9379bb5dadd7"/>
- デリゲートのハンドリング
  - 取得したメディア情報のoffsetを参照して、対象となるoffsetをプロパティにもつインスタンスを特定している
  - <img width="600" src="https://github.com/chocoyama/WWDC/assets/7239831/0e5dc975-0fab-474f-9908-ea1d0e780a4b"/>

＃ Best practices

- `.shazamcatalog` はデバイス間でシームレスに共有できる
- fileURLでディスクからロード・保存することができ、ネットワークを介した配信も可能
- カタログはAppのローカルに構築するので、参照シグネチャーは事前に取得した上でAppが動作する設計にしておくのが良い
  - ※ カスタムカタログオブジェクトとしてaddしておく
