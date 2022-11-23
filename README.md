# swift-knowledge
swift開発中に得た知識、思考を整理するためのリポジトリです

# フレームワーク

志望先企業がどんなフレームワーク使ってるか情報収集しておきたい

参考文献
- [Swiftフレームワークのまとめ【2022年版】](https://freelance-start.com/articles/75) 2022/03
- [Swiftで使えるWEBフレームワーク7選！特徴や使い道まとめ](https://www.sejuku.net/blog/11112) 2021/10
- [Swiftフレームワークおすすめ7選と選び方【2022】](https://freelance.techcareer.jp/skills/47/articles/18991/) 2022/10

## perfect

- フロントエンド、バックエンドどちらの開発にも使える
  - バックエンド開発も勉強できる
- 自身で構築したサーバー上で動作させることが出来る
  - 自由度が高い

## Swifton

- LinuxとMax OSで動作し、Ruby on Railsに影響を受けたWebフレームワークで、Rubyのようなシンプルなコードを書くことが出来る
- MySQLやPostgreSQLのデータベースもサポートしている
- Ruby開発をしたことがある人、これからしたい人d('∀'*)
- マイグレーション機能はまだない
  - データ移行機能

## Slimane

- 非同期通信に強い
- [swift Express](https://grandbig.github.io/blog/2016/07/10/swift-express/)の影響を受けているので動作が軽い
- 自信がサーバーとして動作するため扱いやすい

## Kitura

- BluemixというIBM社のクラウド環境上で動作するWebアプリケーションやWebサーバーを開発することが可能
- 発展途上、今後に期待
- サーバーサイドでswiftを高速に動作させるために開発された
## Express

- とにかく動作が速い
- Ruby on RailsやLaravelと同じ拡張性に優れたMVCによる開発がサポート
- シンプルでテンプレートが提供されているためスムーズな開発が可能
- ド定番すぎてswiftエンジニアは勉強しない手は無い

## Vapor

- MacOSとLinuxのUbuntu上で動作
- ORMやJSON・Validateの充実した標準パッケージを搭載しており、スムーズな開発をすることが出来る
  - なんで？
- クラウドサービスを作るための便利な機能、APIを提供

## HTTPSwiftServer

- Mac OS用アプリのCocoaフレームワークを拡張するためのフレームワーク
- HTTPをiOSアプリと連携出来る
  - だから？
- サーバー機能を使う為の最もベストな方法

## React Native

- JavaScriptのライブラリであるReactを利用してiOSアプリを開発
- 学習コストがかからないこと
  - なんで？
- UI/UXを意識した開発が可能
  - どういうこと？
- React.js・Objective-Cの知識必須
  - 具体的には？

## SwiftMonkey

- Swift 4.0
- iOSアプリケーションのランダム化されたUIテストを実行するために使用
  - どういうこと？

## Chatto

- チャットアプリケーションの作成を主な目的としたSwift用の軽量フレームワーク
- 動作が軽い
- 拡張性と高いパフォーマンスであることやオートローディング時のページネーション、異なる方向へのページネーションもサポートしている
- メッセージ用のセルと拡張可能な入力コンポーネントを含むChattoAdditionsという付属のフレームワークもある

### Apple Developer Docs

## [AVFoundation](https://developer.apple.com/documentation/avfoundation/)

- メディアを再生する

