---
title: 'RailsガイドMEMO #はじめに -Railsをはじめよう-'
date: "2018-04-01"
path: "/railsguides-getting-started/"
---

- 副業でRailsを使う機会があり雰囲気で何となくで書いている部分があったので確認のため読み始めた
- 出来るだけ書き続けれるように最初は雑に書いていく

# Railsをはじめよう

## 1 本ガイドの前提条件

- 特になし
- (Dockerでも用意してみたい)


## 2 Railsとは何か

- > 同じことを繰り返すな (Don't Repeat Yourself: DRY)
- > 設定より規約が優先される (Convention Over Configuration)


## 3 Railsプロジェクトを新規作成する

### 3.1 Railsのインストール

- 特になし

### 3.2 ブログアプリケーションを作成する

- 特になし


## 4 Hello, Rails!

### 4.1 Webサーバーを起動する

- 特になし

### 4.2 Railsに"Hello"と挨拶させる

- 特になし

### 4.3 アプリケーションのホームページを設定する

- `root 'welcome#index'`


## 5 アプリケーションの実装と実行

### 5.1 土台を設置する

- 特になし

### 5.2 最初のフォーム

- 特になし

### 5.3 記事を作成する

- `.inspect`
  - ハッシュの内容を人間に読みやすい文字列にして返します
  - [instance method Hash\#inspect \(Ruby 2\.5\.0\)](https://docs.ruby-lang.org/ja/latest/method/Hash/i/inspect.html)

### 5.4 Articleモデルを作成する

- > Railsのモデルは、単数形の名前を持ち、対応するデータベーステーブル名は複数形で表されるというルールがあります

### 5.5 マイグレーションを実行する

- 特になし

### 5.6 コントローラでデータを保存する

- > チェックされていないパラメータをまるごとモデルに保存する行為は、モデルに対する「マスアサインメント」と呼ばれています
- `params.require(:article).permit(:title, :text)`

### 5.7 記事を表示する

- 特になし

### 5.8 すべての記事を一覧表示する

- 特になし

### 5.9 リンクの追加

- > 現在と同じコントローラのアクションにリンクする場合は、controllerの指定は不要です

### 5.10 検証 (バリデーション) の追加

- [Active Record バリデーション \| Rails ガイド](https://railsguides.jp/active_record_validations.html)
- `@article.errors.any?`
  - エラーが発生しているかどうかをチェック
- `@article.errors.full_messages`
  - エラーメッセージを全文表示
- `pluralize`
  - 数値を受け取ってそれに応じて英語の「単数形/複数形」活用を行ってくれるRailsのヘルパーメソッド

### 5.11 記事を更新する

- > ここで面白いのは、@articleのようなインスタンス変数の代わりに同じ名前のシンボル (:articleなど) を渡した場合にも動作はまったく同じであることです

### 5.12 部分テンプレート(パーシャル)を使用してビューの重複コードをきれいにする

- 特になし

### 5.13 記事を削除する

- 特になし


## 6 2番目のモデルを追加する

### 6.1 モデルを生成する

- > t.referencesという行は、2つのモデルの関連付けを指定するための外部キーを設定します

### 6.2 モデル同士を関連付ける

- > 1つのコメントは1つの記事に属する (Each comment belongs to one article)
  - `belongs_to :article`
- > 1つの記事は複数のコメントを持てる (One article can have many comments)
  - `has_many :comments`

### 6.3 コメントへのルーティングを追加する

- 特になし

### 6.4 コントローラを生成する

- [Rails 新規作成formの作り方~newとbuildの違い~ \- Qiita](https://qiita.com/shizuma/items/5cef6768c5a5d899e54d)


## 7 リファクタリング

### 7.1 パーシャルコレクションを描画する

- > renderメソッドが@article.commentsコレクションに含まれる要素を1つ1つ列挙するときに、各コメントをパーシャルと同じ名前のローカル変数に自動的に割り当てます
- > この場合はcommentというローカル変数が使用され、これはパーシャルでの表示に使用されます

### 7.2 パーシャルのフォームを描画する

- 特になし


## 8 コメントを削除する

## 8.1 関連付けられたオブジェクトも削除する

- > ある記事を削除したら、その記事に関連付けられているコメントも一緒に削除する必要があります
- > Railsでは関連付けにdependentオプションを指定することでこれを実現しています


## 9 セキュリティ

### 9.1 BASIC認証

- `http_basic_authenticate_withメソッド`
  - `http_basic_authenticate_with name: "dhh", password: "secret", except: [:index, :show]`

### 9.2 その他のセキュリティ対策

- [Rails セキュリティガイド \| Rails ガイド](https://railsguides.jp/security.html)


## 10 次に学ぶべきこと

- 特になし


## 11 設定の落とし穴

- > Railsでの無用なトラブルを避けるための最も初歩的な方法は、外部データを常にUTF-8で保存することです


## 12 参考資料

- 特になし


# まとめ

- 最初はだいだいわかってそうだったので飛ばそうと思ったが一応読んだ
- RubyやRailsのメソッドなどの細かい部分でわかってないところが多々ある