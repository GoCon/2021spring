---
key: a5-l
title: Go言語低レイヤー入門 Hello world が画面に表示されるまで
id: a5-l
format: conference
talkType: long_session
level: intermediate
tags:
  - A5-L
speakers:
  - dqneo
videoId: null
presentation: null
draft: false
---
fmt.Print("hello world\n") この hello world がターミナルに表示されるまで、Go言語の処理系でどのようなことが行われているか、考えたことはあるでしょうか？

本トークでは、fmt.Print() の呼び出しを底の底まで探り、Go言語の処理系がOSとどのように相互作用して画面に文字を表示するのかを詳しく解説します。

このトークを聞くことで、あなたは下記の領域へのとっかかりを得ることができるようになるでしょう。

* Go言語とシステムコールの関係
* Goアセンブリの読み方
* 自分でシステムコールを叩く方法
* 自作Goコンパイラの始め方

---
* 最小のプログラムはどう動いてるのか
* Go言語とruntime
* Go言語とシステムコール
* Hello world のシステムコールを見てみよう (strace, gdb, コードリーディング)
* Goアセンブリの読み方
* Hello world を低レイヤー版で書き直す (ライブコーディング)
