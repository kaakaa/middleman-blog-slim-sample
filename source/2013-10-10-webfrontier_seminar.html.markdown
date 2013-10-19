---
title: 2013年秋 Web開発最前線テックトーク
date: 2013-10-10
tags: 勉強会,web
---

### これから始める"Ruby on Rails"2013年秋版

##### 開発環境

- MySQL::Sandboxで複数バージョンのインストールができる

##### テスト

- 現場ではあまりテストは書かれない
- テストする順番を考える

- RSpecが主流(model)
- Request spec(Controller)
  - RoutingをトレースしたControllerのテスト
- Rspec + Capybara + Poltergeist(View)
  - 現状は手作業
  - Capybara 
    - Webアクセス自動化 + テスト
    - DOMを取得
  - Poltergeist(Phantomjs)
    - seleniumの軽量版
    - Capybaraのplugin
    - headlessなのでブラウザを開かずにテストできる

##### 便利なgem

- Rails高速化
  - Springがよく使われていそう
  - 実行ファイルをキャッシュして、デーモンとして別プロセスで活かしておく
  - spork/zeus/commands

- Rubocop(ロボコップ)
  - 静的解析
  - コーディング規約チェック

- TDD
  - guard/watchrが便利

### 最近のnode.jsについて

##### Node

- node
  - sleepやmutexがない。idle
  - ver.偶数メジャーバージョンをインストールする（奇数バージョンはstableじゃない）
  - nodeのサイトにstabilityを調べられる（apiの安定性）
    - gruntのfs.watch -> stableでない

- 再帰処理は気をつける
  - 再帰処理中はconnectionを受け付けられない
  - 他の処理が割り込みできる余地を残しながら回す
  - ✕ nextTick ◯ setImmediate
  - nextTick: イベントループ内でネスト的に再帰処理 / setImmediate:１つのイベントを繰り返す

- Stream2
  - dataイベントがある奴は古い
  - readableイベントがある奴は新しい

- プロセス管理
  - initctl + foreman + grunt

- node-webkit
  - node.jsでGUIアプリFW

- Haroopad
  - markdownエディタ

- node使えばXHR制約を受けないのでGUIアプリが簡単に作れる

- Grunt
  - YAPCのスライドが参考になる

- tessel
  - node.jsが組み込まれたマイコン

- 大学諸島プログラミングの授業がjavaからjavascriptに変わった
  - 初学者を組み込みやすい

- Glideのサーバは
  - さくら使ってる間はスローダウンさせられてログインできずに落ちてた
  - 自宅サーバで動かしてる

- process memoryusage
  - でメモリ使用量が見れる

### ScalaでのWeb開発事情

- gitbucket
  - Gitlabのインストールがめんどい。メンテする気にならない
  - JGit
  - httpでしかアクセスできない(sshはダメ)

- Scalaの利点
  - 安全性 / 柔軟性

- Scalaフレームワークの使い分け
  - Slick (タイプセーフにDSL記述・DB接続)
  - Play2 -> Netty(多重度やスケールアウトに強い) / Scalatra -> Tomcat()
  - SIerはスケールとかいらないのでScalatra(Tomcat)

- Play2
  - ORM微妙(とても微妙/play2.3からはslickが標準に)
  - 既存Javaのポーティングに向かない
  - テンプレート/ルーティングもタイプセーフ
    - テンプレートがタイプセーフなJavaのwebFWはない
  - ステートレス
    - セッションの書き換えは変態的な記述が必要
  - すべてをノンブロッキングで作れる
  - Websocketを簡単に使える

- Scalatra
  - servletAPIを持っているので既存のjavaコードとの移行性も高い
  - play2のタイプセーフなテンプレートエンジンを単体で使える

- Slick
  - タイプセーフなDSL（Lynqみたいなやつ）
  - テーブル定義を簡単にするアノテーションも提供されている

- デメリット
  - コンパイルが遅い
    - 修正だけ差分コンパイルも可能
    - プロジェクトを細かく分ける（コンパイル単位を小さく）
    - 依存を脚力減らす（差分コンパイルのために）
    - Scalaコミュニティでも最大の問題として認識されている
  - バイナリ互換性がない
    - Scalaをバージョンアップするとバージョンの古いバイナリが動かなくなることがあるA
  - 周辺ツールが未成熟
    - IntelliJおすすめ
      - Eclipseのようにホワイトアウトしない
    - sbtも微妙
      - キャッシュの挙動がおかしい
      - sbtもあまり互換性がない


### JavaScript フロントエンド開発の昨今





