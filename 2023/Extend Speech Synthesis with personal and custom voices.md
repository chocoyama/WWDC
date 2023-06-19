# SSML

- SSMLは、音声テキストを表現するためのW3C標準
- <img width="631" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/3bc94300-51a1-4af6-a132-770e21266279">

# Speech synthesizer

- あるテキストと、希望する音声特性に関する情報をSSMLの形で受け取り、そのテキストの音声表現を提供する
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/97db9028-3c14-40e9-82ac-ec645549d5ea">
  - <img width="619" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/17aa5023-177a-4ac2-9031-1fb9f3111132">
- `Audio Unit Extension` を追加して実装する
  - そのため、ホストプロセスではなく、拡張プロセスの中で実行される
- （実装方法は動画内で詳しく説明されている）

# Personal Voice

- <img width="618" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/e8f4043c-d27b-4676-922c-1ff6cdce4b50">
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC2023/assets/7239831/646ce5e1-1307-4a43-9851-cf95ea9da7a4">
- 現状、英語しか対応していないらしい
  - 参考：https://www.toyship.org/2023/06/14/152838
