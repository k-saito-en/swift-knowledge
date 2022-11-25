# フレームワーク

**ここでやっていること**

- 志望先企業がどんなフレームワーク使ってるか情報収集しておきたい
- ポートフォリオアプリ作成のフレームワーク選定に役立てたい

**参考文献**
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

<br />
<br />
<br />
<br />
<br />

----------

# 機能実装

**ここでやっていること**

エラー解決・やりたいことの実現方法調査
1. 原因不明のエラー・実装したいコードに遭遇　
1. [StackOverflow](https://stackoverflow.com)で調べる（英語の方が効率良さそう→英語圏のユーザーが大多数だから必然的に質問数も英語のものが多い）
1. バージョンを確認し、獲得票数トップ３を比較
1. [Apple API Docs](https://developer.apple.com/documentation/technologies)で、調査結果のコードが何をするものなのかを解析
1. アウトプットし、自分に必要な、最適な形に整形し実装

実装してみた機能のアウトプット

## アプリでボタン押下時に音を再生する

```swift
import UIKit
//AVリソースの処理詰め合わせキットのインポート
import AVFoundation

class ViewController: UIViewController {
    
    //player変数にAV再生オブジェクトを格納
    var player: AVAudioPlayer!
    
    //viewがロードされた時の処理を記述
    override func viewDidLoad() {
        super.viewDidLoad()
        
    }
    
    @IBAction func keyPressed(_ sender: UIButton) {
        
        //押下されたボタンの名前を引数に関数呼び出し
        playSound(soundName: sender.currentTitle!)
        
    }
    //string型のsoundNameを受け取って、リソース名と照らし合わせて再生する関数
    func playSound(soundName: String) {
        //BundleでAVファイルをURLに変換
        let url = Bundle.main.url(forResource: soundName, withExtension: "wav")
        //受け取ったURLから「AVプレーヤーを作成」する
        player = try! AVAudioPlayer(contentsOf: url!)
        //作成されたプレーヤーを起動する
        player.play()
        
    }
    
}
```
## 乱数を生成

[Random Unification SE-0202](https://github.com/apple/swift-evolution/blob/master/proposals/0202-random-unification.md)がSwift 4.2で実装

### 整数の乱数を生成して、switch if-elseで表示文言分け

```swift
func loveCalculator() {
    let loveScore = Int.random(in:  0...100)
    
    switch loveScore {
    case 81...100:
        print("You love each other like Kanye loves Kanye.")
    case 41..<81:
        print("You go togather like Coke and Mentos")
    case ...40:
        print("You'll be forever alone")
    default:
        print("Error lovescore is out of rabge.")
    }
    
    if loveScore == 100 {
        print("You love each other like Kanye loves Kanye.")
    }else{
        print("You'll be forever alone")
    }
}

loveCalculator()
```

### 独自のRandomNumberGeneratorを作って使う

```swift
struct MyRNG: RandomNumberGenerator {
    // RandomNumberGeneratorの実装
}
```
```swift
public protocol RandomNumberGenerator {

    //符号なし 64 ビットのランダム値を返す
    public mutating func next() -> UInt64
}

extension RandomNumberGenerator {

    //Tの範囲内の乱数を返す
    public mutating func next<T>() -> T where T : FixedWidthInteger, T : UnsignedInteger

    //T以下の乱数を返す
    public mutating func next<T>(upperBound: T) -> T where T : FixedWidthInteger, T : UnsignedInteger
}
```

そして作ったRandomNumberGeneratorを各関数のパラメーターに渡す。

```swift
var myRNG = MyRNG()
let value = Int.random(in: 1 ..< 5, using: &myRNG)
```

## UIButton押下時に0.2秒だけボタンを半透明にする

やっぱりkeyPressed関数内での実装で良かったんだ！

調べるときにXcodeも検索クエリに含めないと「１から実装する方法」ばかり出てきた。。。

```swift
@IBAction func keyPressed(_ sender: UIButton) {
        
        playSound(soundName: sender.currentTitle!)
        
        //誰の.何を=どうする　押下情報が送られてきたボタンの色の濃さを半分にする
        sender.alpha = 0.5
        
         //ボタン背景が半透明になる時間を0.2秒に指定
        DispatchQueue.main.asyncAfter(deadline: .now() + 0.2) {
            //色の濃さを元に戻す
            sender.alpha = 1.0
        }
        
    }
```
## UIButtonから取得した値から秒数別にカウントダウン
```swift
import UIKit

class ViewController: UIViewController {
    
//  卵の硬さ別の茹で時間を辞書に格納
    let eggTimes = ["Soft" : 300 ,"Medium" : 420 ,"Hard" : 720]
    
//  初期値は60秒
    var secondsRemaining = 60
    @IBAction func hardnessSelected(_ sender: UIButton) {
        
//        押したボタンのタイトルを取得　！で無理やり開封
        let hardness = sender.currentTitle!
        
//        設定した変数を硬さ別の残り時間に上書き　！で無理やり開封
        secondsRemaining = eggTimes[hardness]!
//        TimerクラスのscheduledTimerメソッド
//        パラメータ
//        timeInterval:カウント間隔
//        selector:関数の名前を指定してtimeIntervalごとに実装内容を呼び出す
//        repeats:タイマーを繰り返すかどうか　bool
        Timer.scheduledTimer(timeInterval: 1.0, target: self, selector: #selector(updateTimer), userInfo: nil, repeats: true)
            
    }
//  selectorはObjective-C由来なので@objcアノテーションが必要
    @objc func updateTimer(){
        
        if secondsRemaining > 0{
            print("\(secondsRemaining) seconds.")
            secondsRemaining -= 1
        }
    }
```
