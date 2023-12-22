## 事前準備について
### 事前準備1.リモートリポジトリの作成
https://github.com/ にてGitHubにログインした後，新しくリポジトリを作成してください．  
GitHubアカウントについては実験用フォルダのREADME.txtを確認してください．  

### 事前準備2.ngrokの実行
事前にインストールされているngrokを起動し，ngrokのターミナルにて以下のコマンドを実行してください．  
```
ngrok http 5000
```
コマンド実行後に表示される項目のうち，[**Forwarding**]に記載されている[**https://**]から始まるURLを範囲選択し，コピーしてください．  
※[**Forwarding**]は二つ項目がありますが，[**http://**]ではなく[**https://**]から始まるURLをコピーしてください．  

### 事前準備3.Webhookの設定
先ほど新しく作成したリポジトリ上部の[**Setting**]の項目をクリックし，左の項目から[**Webhooks**]を選択してください．  
[**Add webhook**]を選択し，Webhookの設定を完了してください．  
変更点は以下の通りです．
  
**Payload URL**：先ほどコピーしたngrokのURL  
**Content type**：application/json  
[**Let me select individual events.**]を選択し，[**Pull requests**]にチェック  

### 事前準備4.Collaboratorの追加
リポジトリのページから[**Settings**]→[**Collaborators**]と移動し，共同開発者の追加を行う．  
[**Add people**]をクリックし，ユーザー名を入力して共同開発者を追加する．  
共同開発者のユーザー名については実験用フォルダのREADME.txtを確認してください．

### 事前準備5.Pythonの実行
実験用フォルダ内の**app.py**および**server.py**をコマンドプロンプトから実行してください．  
その際，仕様上の観点から，**app.py**を実行するプロンプトと**server.py**を実行するプロンプトの二つのウィンドウを立ち上げてください．  
実行の際のコマンドは以下の通りです．  
[app.py]
```
python app.py
```
[server.py]
```
python server.py
```

### 事前準備6.Unityの実行
実験用フォルダ内の**GitCollabSim.exe**を起動してください．  
以降はGitCollabSim内の説明および以下に従って実験を進めてください．

## 実験について
### [注意1]
本実験はあくまでもGit/GitHubの使用方法の学習について調査するものです．被験者のプログラミング能力を測るものではありません．  
そのため，実験における**各ファイルの変更はすべて以下に記載**しているので，それに従って実験を進めてください．  
**コピペ推奨**です．  

### [注意2]
javaファイルですが、UTF-8でエンコードしています．  
コンパイル時にうまく動作しない場合があるので以下のコマンドでコンパイルしてください．
```
javac encoding utf-8 [ファイル名]
```

### 1.チュートリアル
チュートリアルでは，ローカルリポジトリとリモートリポジトリの連携などの初期設定を行います．  
また，以降のシナリオで使用するGitのコマンドについて練習を行います．

### 2.正常系シナリオ
正常系シナリオでは，実際に共同開発を疑似体験しながらGitのコマンドについて学びます．  
課題1はコードを実装しプルリクエストを作成してください．  
課題2はBotによる実装が行われるので正しく実行できるか確認しましょう．  

#### 課題1 GameMain.javaで文章の表示
[変更するファイル]GameMain.java
```
[変更内容](変更箇所のみ抜粋)
  public static void main(String[] args) {
    int playerHand;
    // 課題1 文章の表示
    System.out.println("1:グー 2:チョキ 3:パー");
    System.out.println("じゃんけん...");
```
```
[実行例]
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
```

#### 課題2 Playerの手の決定とその表示
[変更するファイル]　GameMain.java, Hand.java
```
[変更内容](変更箇所のみ抜粋)
・GameMain.java
    // 課題2 Playerの手の決定とその表示
    // HandクラスのgetHandNameメソッドを使ってPlayerの手を表示する
    if (args.length == 1) {
      playerHand = Integer.parseInt(args[0]);
    } else {
      System.out.println("コマンドライン引数でプレイヤーの手を決定して下さい");
      return;
    }
    System.out.println("プレイヤー : " + Hand.getHandName(playerHand));

・Hand.java
    // 課題2 Playerの手の決定とその表示
    // 1ならば"グー",2ならば"チョキ",3ならば"パー"を返す
    if (hand == GU)
      handName = "グー";
    else if (hand == CHOKI)
      handName = "チョキ";
    else if (hand == PA)
      handName = "パー";
```
```
[実行例]
$ java GameMain 1
1:グー 2:チョキ 3:パー
じゃんけん...
プレイヤー : グー

$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
コマンドライン引数でプレイヤーの手を決定して下さい
```

### 2.異常系シナリオ
異常系シナリオでは，共同開発中に障害が発生するため，その対処法を学びます．  
課題3はコードを実装しプルリクエストを作成してください．  
課題4はBotによる実装が行われますが，障害が発生するので，正しく対処したのち，実行できるか確認しましょう．  

#### 課題3 Computerの手の決定とその表示
[変更するファイル]　GameMain.java, Computer.java  
```
[変更内容](変更箇所のみ抜粋)
・GameMain.java
    // 課題3 Computerの手の決定とその表示
    // ComputerクラスのdecidesComputerHandメソッドとHandクラスのgetHandNameメソッドを使ってPlayerの手を表示する
    int computerHand = Computer.decidesComputerHand();
    System.out.println("コンピュータ : " + Hand.getHandName(computerHand));

・Computer.java
    // 課題3 Computerの手の決定とその表示
    // Randomメソッドを使って1~3の数値を返す
    Random random = new Random();
    int rnd = random.nextInt(3) + 1;
    return rnd;
```
```
[実行例]
$ java GameMain 1
1:グー 2:チョキ 3:パー
じゃんけん...
プレイヤー : グー
コンピュータ : パー
```

#### 課題4 勝敗判定とその表示
[変更するファイル]　GameMain.java, VictoryOrDefeat.java  
```
[変更内容](変更箇所のみ抜粋)
・GameMain.java
    // 課題2 Playerの手の決定とその表示
    // HandクラスのgetHandNameメソッドを使ってPlayerの手を表示する
    if (args.length == 1) {
      playerHand = Integer.parseInt(args[0]);
    } else {
      System.out.println("コマンドライン引数でプレイヤーの手を決定して下さい");
      return;
    }

    // 課題3 Computerの手の決定とその表示
    // ComputerクラスのdecidesComputerHandメソッドとHandクラスのgetHandNameメソッドを使ってPlayerの手を表示する
    int computerHand = Computer.decidesComputerHand();

    // 課題4 勝敗判定とその表示
    // 課題2,3において実装したPlayerおよびComputerの手の表示はVictoryOrDefeatクラスに移動する
    VictoryOrDefeat.decisionVictoryOrDefeat(computerHand, playerHand);

・VictoryOrDefeat.java
    // 課題4 勝敗判定とその表示
    // 課題2,3においてGameMain.javaに実装したPlayerおよびComputerの手の表示は以下に移動する
    System.out.println("プレイヤー : " + Hand.getHandName(playerHand));
    System.out.println("コンピュータ : " + Hand.getHandName(computerHand));

    // int型のplayerHand,computerHandを使って勝敗判定を表示する
    if (playerHand == computerHand) {
      System.out.println("あいこ");
    } else if ((playerHand == 1 && computerHand == 2) || (playerHand == 2 && computerHand == 3)
        || (playerHand == 3 && computerHand == 1)) {
      System.out.println("勝ち");
    } else {
      System.out.println("負け");
    }
```
```
[実行例]
$ java GameMain 1
1:グー 2:チョキ 3:パー
じゃんけん...
プレイヤー : グー
コンピュータ : パー
負け

$ java GameMain 2
1:グー 2:チョキ 3:パー
じゃんけん...
プレイヤー : チョキ
コンピュータ : チョキ
あいこ

$ java GameMain 3
1:グー 2:チョキ 3:パー
じゃんけん...
プレイヤー : パー
コンピュータ : グー
勝ち
```
