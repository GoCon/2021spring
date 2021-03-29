---
key: b6-l
title: Goの構造体とタグを極める
id: b6-l
format: conference
talkType: long_session
level: advanced
tags:
  - B6-L
speakers:
  - yoshiki_shibukawa
videoId: null
presentation: null
draft: false
---
Goで大規模アプリケーションを作るためのビルディングブロックは、構造体とタグです。手続き的なコードを減らし、宣言的に解決する手法はGoをエンタープライズ開発で活用するためにますます必要となると思いますが、自作するにはタグを処理するコーディングは多数の型を網羅するコーディングが必要で長くなります。本プレゼンでは、Goプロジェクトを牽引する「アーキテクト」クラスの開発者を対象に、reflectパッケージを使ったタグ処理のパターンを紹介するとともに、タグ処理関数を実装するための考え方、ロジックなどを紹介します。

説明は日本語、資料は英語で発表します。

---

Goではリフレクションよりも静的なコード生成を重視する文化ですが、
reflectパッケージが多様される数少ない活躍の場が構造体のタグの処理です。
Goを業務で使ったことがあれば、encoding/jsonを使ったマッピングや
RDBのレスポンスのマッピングなどでその恩恵に授かったことがある人が
ほとんどだと思います。

実装の効率を高めるには、汎用的なユーティリティを作成して少ない行数で
ロジックを実現できる、繰り返し実装を減らしてミスを減らすなど、
コーディングのテクニックで改善できるものもありますが、タグを使った
宣言的記法を使う方法もあります。高度なタグ処理関数を実装することは
一定以上の品質のプログラムを一定の速度で作り続けるには極めて有効な
方法です。

ざっとタグの活用例をリストアップしたのが次の項目です。

* DBのマッピング
* envconfigで環境変数のマッピング
* JSON/YAMLなどのマッピング
* バリデーション
* 比較

まず、タグ処理のロジックを4つのパターンに類型化し紹介します。それぞれ、
どのようにタグを探索して処理していくのかを説明します。

* インスタンスの要素を探索する「ビジター」
* 構造体にデータを割り当てる「デコード」
* 構造体からデータを取り出す「エンコード」
* 複数のインスタンスの要素同志を処理する「ランデブー」

これらのパターンの実装にあたってはreflectパッケージを使います。
構造体の探索の仕方のコツや、構造体のフィールドからの値の読み込み
フィールドへの値の設定について、さまざまなバリエーションを網羅
する書き方を紹介します。

最後に、実用的なサンプルとして、*http.Requestの各要素（JSONの
ボディだけではなく、ヘッダーやクッキーなども）を構造体にマッピング
するコードを紹介します。

タグの活用の幅は、現時点でライブラリがある領域にとどまらない
と思いますが、コーディングで気をつけなければならないことも多く、
その割に現時点でタグ処理のコードを書くための情報が十分にあるとは
言えないと思います。

本発表を通じて、仕事の流れを作るようなアーキテクトクラスの開発者、
少ないコーディング量で使えるようなライブラリを実装したいと
考えているライブラリ作者の人たちに、Goらしさを持った
宣言的なコーディングテクニックを提供します。