# コンピュータービジョン

- <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6e7765d4-8273-4e75-b966-4cf344f475ac">
- <img width="606" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/db5d5768-e798-4894-8141-4907552b46d8">

# Core Image

- Core ImageはMetal上に構築され最適化された、使いやすい画像処理フレームワーク
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/94a091d4-569c-40d4-a8d3-1fa318f04236">
  - Visionへの入力の前処理をすることで、アルゴリズムをより速く、より堅牢にすることができる
  - isionからの出力を後処理することで、結果をユーザーに表示する新しい方法をアプリケーションに提供できる
- 分析用に画像を処理する最良の方法の１つは、最高のパフォーマンスを得るために画像を縮小すること
  - 総合的に最高の品質を持つスケーラーはCILanczosScale
  - <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/389b5a7e-aa9a-4b66-9136-8c76bd01d2bf">
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/acb2b3bb-2e64-4bd6-8019-eb59e02a51a9">
- CIMorphologyRectangleMaximumを使用して ダイレートを実行すると 画像の明るい領域が大きくなる
  - <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/abbc25b2-22f1-49fd-b70e-592badc230c6">
- CIMorphologyRectangleMinimumを使用して エロードを実行すると 明るい領域が小さくなる
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b15b8023-b32e-4ed5-a9ed-34a55c2bd67e">
- CIMorphologyRectangleMinimumに続いて CIMorphologyRectangleMaximumを使用し、Closeを実行する
  - これは、アルゴリズムに影響を与える可能性のある小さなノイズ領域を、画像から削除する場合に非常に便利
  - <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/fe4a0172-ed3d-4350-8f14-4e627ac5bbb3">
- 一部のアルゴリズムではモノクロ入力のみが必要
  - この場合、Visionは自動的にRGBをグレースケールに変換する
  - 入力画像に関するドメインの知識がある場合は、CoreImageを使用してグレーに変換するとよりよい結果が得られる可能性がある
  - <img width="619" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6ae9b4cc-a338-498d-9af5-1529fc15e7c9">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d13e618a-6605-4cf5-9f4f-7e6d321de168">
- 画像解析前のノイズ低減も考慮する必要がある
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/94e85093-0a4e-49cd-bdcd-115e981f8ade">
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/53e8ea5c-d784-4cf4-9170-6120762fcb08">
  - <img width="612" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5071ed7d-93b2-468d-8b08-d3a82dcc4160">
- エッジ検出フィルタ
  - <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d2de7e94-5d0e-4ec4-aca1-2918d7d855d5">
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/90d4c420-65b3-4ccb-82bc-c486ee6b73b3">
  - CLGaborGradientsを使うと、ノイズに対する耐性が高い2Dグラデーションベクトルが生成される
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9b3a5b8a-9cdc-4b68-ac12-d5bdea655027">
  - <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/25b86ccf-59ee-416c-848f-dea01eeac197">
- 画像を白黒にする新しいフィルタ
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e2d37dcc-f862-4755-9784-8cae087f66d8">
- 2つの画像を比較するためのフィルタ
  - <img width="612" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/68991402-c54a-41f0-8ef5-73cefe3f1618">
  - <img width="614" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/95ab9c69-68da-44f0-9f13-65aff5dd5087">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/162df01a-18f3-4508-886c-7057d996704d">
- ドキュメント
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0820e903-0569-406b-a98c-91943c1bee45">

# カラースペース

- CoreImageを使用すると、多様なカラースペースに対応する作業が非常に簡単になる
  - CoreImageは自動的に入力を機能しているスペースに変換する（非クランプリニア Bt.709プライマリなど）
- ただし アルゴリズムでは別のカラースペースの画像が必要になる場合がある
  - その場合は、CGColorSpaceから使用したいカラースペースの変数を取得し、image.matchedFromWorkingSpaceを呼び出す
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/294235f3-0ec8-4c61-a68d-c8c51bfe8ab9">

# Visionからの出力を後処理する

- バーコード認識からバーコード画像を生成
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dc456dfd-18e4-4750-a3fe-3f796ceb1c73">
- Visionの顔認識に基づいてフィルタを適用
  - 意識する必要があることは、Visionの正規化座標系から、CoreImageのデカルト座標系に変換することだけ
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/7a6b5463-b4f8-46c7-82c9-9978103d275f">

# Vision

- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/318fa55b-6262-40e4-8fad-7f665f7dcce6">
- <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e8226e5a-b2b3-421f-b120-25254e5dd25a">
- <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/efd48055-e0a9-4145-b830-dc179c37e8f6">
- <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8079d64f-e367-48d5-9533-d4c656e7d90e">

# Contour Detection

- <img width="609" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/28409cf0-c12a-4878-bf3d-3e2eab4da740">
- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d47807cd-dccf-4c49-ad7e-8fc0e22232dd">
- <img width="611" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5a93a770-2033-46e5-8cc2-d6e0691cb196">
- <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/da0529fe-79b3-4384-8055-baa13885185a">
- <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/62e518a3-b459-4a7f-a5c6-7d267e9c83fb">
- <img width="615" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9cbd3cf1-c867-4f71-88f6-9a20cd46fafe">
- <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/26e34dbd-630f-4c83-9029-46e1fff6dbd7">
- 画像処理
  - 画像をロードする必要がありので、CGImageSourceを使用してUIImageを取得し、CIImageにロードし名前を付ける
  - 次にCoreImageを使用して、CIFiltersにより画像を処理する
  - CIAbsoluteThresholdまたは他の多くの場合と同様
- 画像分析
  - 処理したCIImageからVNImageRequestHandlerを作成する
  - 次にVNDetectContourRequestのようなリクエストを実行する
  - 画像を前処理する必要さえないかもしれないところが利点
- 結果の視覚化
  - CoreImageを使用して、実際に持っている画像の上に同じコンテキストで直接合成できる
  - CIMeshGeneratorまたはCITextGeneratorを使用可能

# Optical Flow

- ２つのフレーム間の移動を解析したい時、従来はレジストレーションを使用して画像全体の位置合わせを行っていた
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/50b0b627-7659-412c-8a0c-aa1f6aa5c5a4">
  - 2つの画像間の位置合わせができる
- <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1fb0eb46-9d4b-426d-b74e-adac99fd67b2">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/09e7b9e3-bd40-4a32-a4e9-91a178b41add">
- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/fd316a03-fc68-49d0-bd31-a40326e6cfc5">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/9a507b20-51e5-40a9-867f-bfe77c9d340c">
- <img width="659" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2964810e-3a51-4e69-8416-ea41a3c16f1d">
- <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/01d9a1c8-9ce6-4cad-bc42-cebc05c71392">





