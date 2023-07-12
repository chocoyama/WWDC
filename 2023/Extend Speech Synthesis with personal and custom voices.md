# SSML

- SSMLは、音声テキストを表現するためのW3C標準
- <img width="631" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f2bf8ad6-e051-4c4a-b7e3-5007bb6330da">

# Speech synthesizer

- あるテキストと、希望する音声特性に関する情報をSSMLの形で受け取り、そのテキストの音声表現を提供する
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/19a0d04e-3235-4ad2-a598-c3085ec5ccbb">
  - <img width="619" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6bb3302e-4c7d-4bef-8d67-4d268684bd25">
- `Audio Unit Extension` を追加して実装する
  - そのため、ホストプロセスではなく、拡張プロセスの中で実行される
- （実装方法は動画内で詳しく説明されている）

# Personal Voice

- <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6253baf3-adb0-418c-8a4d-c5960dc95b0a">
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/c22c23fc-faa4-4a9b-b2cb-14dc95dea9c1">
- 現状、英語しか対応していないらしい
  - 参考：https://www.toyship.org/2023/06/14/152838
