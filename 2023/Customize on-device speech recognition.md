# 仕組み

- <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a7636db1-d06b-4993-a073-72e12e5bd82f">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2aeb5b49-058d-403b-be29-107109050deb">

# カスタム言語モデル

- iOS17から言語モデルをカスタマイズ可能に
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0c79b0c2-7459-47e8-bb23-ee74c597230a">

# データ作成

- App内で発話される可能性の高い文章やそのテンプレート登録しておくことができる
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/426cdc94-e3df-4285-a1eb-f8363b32d35b">
- アプリが専門用語を使用する場合などは、それらの用語のスペルと発音の両方を定義し、その使用法を示すフレーズを提供することができる
  - <img width="632" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d922b467-6921-43ad-8bdf-4cb5bab02ff3">
  - 発音はX-SAMPA文字列の形式で受け渡す
  - 各ロケールは発音記号の一意なサブセットをサポートしている
- 実行時に学習させることも可能

# デプロイ

- ファイルを読み込んで、オンデバイス認識の設定をONにする
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d2aa52f1-3592-422e-aa48-617649d4b2e3">
- この時、重たい処理になる可能性があるのでメインスレッドで実行しないように
