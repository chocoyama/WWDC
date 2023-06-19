- ４つの新機能
  - サリエンシー
  - 画像分類
  - 画像類似
  - フェイスクオリティ
- 新しい検出機能と改善されたCoreML
  - オブジェクトトラッキング
  - 顔ランドマーク
 
# Saliency

- 以下の2種類がある
- 注意力ベース
  - 人の感覚に近い
  - 人が何枚かの画像を見た際 最初に目線がいくところを基にモデルが作成されます
  - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b19598f6-da94-400f-92f2-32b8e055f36f">
  - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/748dd807-0285-42b9-9563-7594aa7bb658">
  - こちらの方が「人間らしい要因」によって確定するため、複雑な構造
    - 何が人間らしいかを決める主な要因
      - コントラスト
      - 顔
      - 被写体
      - 視野
      - 光
    - 物体が動くとその影響を受けることがある
- 物体ベース
  - 前景に写る物体や被写体を際立たせる
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/4245d574-aa40-4eab-85cb-d79759f2f7cc">
  - <img width="633" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/14efca81-3fbc-40d6-88e9-6d3291ee128b">
- Heatmap
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/28a42162-7e8d-44cd-8b9b-029acbbcfba1">
  - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/bb1bf15f-248d-4bad-b291-d9fc27f63ee9">
- Bounding Boxes
  - 画像内の突出した全ての部分を四角で囲む
    - 注意力ベースの場合は箱の数は常に１つ
    - 物体ベースの場合は最大３つまで
  - <img width="629" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a4abce15-d9ca-4b37-9290-719ef8eac102">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/86a95acd-308c-4be2-9a27-6fe78c165fe8">

# 活用方法

- サリエンシーでのマスキング
  - ヒートマップを利用
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1ae29bf9-6c11-40ce-8428-da8e3d1c4777">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/ca13e589-3cf4-46a8-b273-a779b8e18415">
- 適切な位置のズーム
  - <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d9c7dbfc-b4f8-479e-993c-40f4d9f761a5">
- 物体認識
  - Bounding Boxesを得て画像をトリミングする→それを画像分類のアルゴリズムに喰わせて分類する
  - <img width="613" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3d2bb292-aa7e-4415-b4ce-1df2c2563050">

# Image Classification

- Taxonomy
  - 分類器による分類法を タクソノミーと言う
  - Taxonomyはクラス間に 直接関連する階層構造を持つ
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/d3f72455-3c77-435b-a72a-d8cb99312300">
- 分類の実行
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/93c80559-6609-419d-862f-ece888159346">
- 閾値の決定
  - クラスにおけるコンフィデンスを得た際、通常それを特定の閾値と比較する（動作基点と呼ばれるもの）
  - どう閾値を設定すべきか
    - 閾値を低く設定すると、対象としたくない画像も対象になってしまう（高想起検索）
      - <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/70594f3d-6426-489a-b100-0f7318aec4c9">
      - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/341ea79a-65ec-48fe-842e-c2e84cf12d62">
      - 実際の動作起点はクラスによって異なる
      - フィルタは自動的に、Taxonomy内でネットワークがどう実行されるかを内部検査し、その結果で動作起点を決める
      - そのため、操作したい想起のレベルを特定するだけで問題ない
    - 閾値を高く設定すると、対象としたい画像が対象外になってしまう（高精度検索）
      - <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/807109fc-b059-4ec2-a42b-172d10f3f51e">
      - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0be4eb34-ab62-44b4-bc3d-ee6abe67b0e1">
    - 高想起検索と高精度検索のバランスを考えた、2つの妥協点の探し方
      - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3e3ecd68-bbe8-4f1e-9a5e-653b88dc1bf4">
      - <img width="622" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/66366e49-0efb-41f5-98ff-51770dd83637">
      - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e87588d6-8530-42a8-a20e-edb4bc57cb76">
      - <img width="794" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/e3d34e43-2401-43b9-98f1-288fb4ccec4e">
      - <img width="784" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/fccb6ce3-3eed-47d7-8250-20b38391fcaf">

# Image Similarity

- 画像の中身を説明する方法、得られた説明を比較する方法を意味する
- 「特徴点」を用いて比較する
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/8ea67228-3e26-4d57-a83d-5a67d044b5d7">
  - <img width="630" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b53a27a3-91f5-4b1b-922f-3e6450ab6bca">
  - <img width="620" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/473203c7-3072-4c52-b62a-cab310e90ff7">
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b957a7ea-cf78-45fd-b827-848f29583ca6">
  - <img width="618" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/841a0a1d-9587-49be-9e04-92db2c073f63">

# Face Technology

- Face Landmarks
  - <img width="601" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/7e0f7838-b7f1-4d8b-8ee1-3df80ceadc0e">
  - ポイントごとのコンフィデンス値も出せるようになった
  - <img width="621" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0ac1aae1-71b5-4321-b321-842f2c2b147a">
  - <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/ecca265e-9d98-47b0-9819-78f9d986c976">
  - <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/28b79b68-c655-48b3-886a-e8b7c546abc1">
- Face Capture Quality
  - <img width="616" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/c03cd19b-d1a5-487f-9a5d-81b0da34de9f">
  - <img width="623" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/86f5ebc1-3203-401d-934d-10b073928624">
  - 閾値として使うべきではない
    - <img width="606" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/6c9fa3b0-cb48-4577-9bd7-b1daf20232f2">
  - 同じ物体を比較、もしくはランク付けをする際の基準です（キーワードは“比較”と“ランク付け”）

# Human Detector

- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/437683fc-fbfa-4b50-91e2-a9812ac40876">
- <img width="617" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b7d58d10-208c-4a98-9acb-ec189b7865fe">
- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/46a7ccd3-9120-455d-8269-171de82f824b">

# Tracking

- <img width="611" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/a328232e-093a-48c3-b700-f6cedddc2ebd">
- <img width="619" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/62f9ab79-c5d4-48d8-865b-c77ae558d540">

# VisionとCoreMLの統合

- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/18e1f181-b1f5-4771-ab9e-f9a10a70577b">
