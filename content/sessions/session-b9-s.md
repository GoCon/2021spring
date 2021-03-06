---
key: b9-s
title: 検索エンジン自作入門
id: b9-s
format: conference
talkType: short_session
level: all
tags:
  - B9-S
speakers:
  - kotaro_adachi
videoId: null
presentation: null
draft: false
---
仕事でElasticsearchを使っているエンジニアが全文検索技術を学ぶためにGoで全文検索エンジンの自作に入門しました。全文検索エンジンは実装が難しいものと思いきや、シンプルな全文検索エンジンであれば簡単に実装できてしまうということを聴衆に伝え、全文検索エンジンを実装や情報検索に興味を持っていただける発表を行います。対象聴衆は「転置インデックス」という単語を聞いたことがあるくらい検索初心者です。Goでの形態素解析についてや連結リストでの転置インデックスの実装についても触れる予定です。

---
# はじめに
技術面とプロダクト面の面白さから情報検索への興味が強いため、さらに詳しくなりたいと思い検索エンジンの自作をはじめました。
検索エンジンの仕組みは大雑把に知っていましたが、実際に自分で作ってみると勉強になることが多かったです。
発表を通じて検索エンジンの技術的な面白さと、既にあるものを自作する楽しさについて触れていきます。

# 対象
全文検索エンジンをなんとなく使っていて、もう少し詳しく知りたい人
検索エンジンを自作したい人
検索が好きな人

# アウトライン
- なぜ検索エンジンを実装するのか
- Indexerの実装
    - インデックスの圧縮
    - 連結リストを用いた転置インデックスの実装
    - 転置インデックスの永続化
- Searcherの実装
    - スコア計算
- Analyzerの実装
    - Analyzerの設計
    - Goでの形態素解析の紹介 
