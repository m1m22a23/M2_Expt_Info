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
リポジトリのページから[**Settings**]→[**Manage access**]と移動し，共同開発者の追加を行う．  
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
### [注意]
本実験はあくまでもGit/GitHubの使用方法の学習について調査するものです．被験者のプログラミング能力を測るものではありません．  
そのため，実験における**各ファイルの変更はすべて以下に記載**しているので，それに従って実験を進めてください．  
**コピペ推奨**です．  

### 1.チュートリアル
チュートリアルでは，ローカルリポジトリとリモートリポジトリの連携などの初期設定を行います．  
また，以降のシナリオで使用するGitのコマンドについて練習を行います．

### 2.正常系シナリオ
正常系シナリオでは，実際に共同開発を疑似体験しながらGitのコマンドについて学びます．  

#### 2-1.

#### 2-2.

### 3.異常系シナリオ
