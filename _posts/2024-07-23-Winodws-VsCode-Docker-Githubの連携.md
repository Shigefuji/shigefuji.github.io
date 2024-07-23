
# VSCodeと、Docker、GitHubの連携方法

## はじめに

このブログでは、Windows上でDockerコンテナを使用してVSCodeで開発し、そのコードをGitHubにコミットする方法を説明します。以下の手順に従って、開発環境をセットアップし、コードを管理するプロセスを理解しましょう。


## インストールと準備
### 1. Dockerのインストール

まず、DockerDesktopをインストールします。公式サイトからダウンロードしてインストールしてください。
・windowsでは、WOL2(Windows Subsystem for Linux)が必要です。 DockerはWSL2でサポートされています。

[Docker公式サイト](https://www.docker.com/products/docker-desktop/)

### 2. VSCodeのインストール

次に、Visual Studio Code (VSCode) をインストールします。こちらも公式サイトからダウンロードしてインストールしてください。

[VSCode公式サイト](https://code.visualstudio.com/)

### 3. Docker拡張機能のインストール

VSCodeには、Dockerを使用するための拡張機能があります。VSCodeを開き、拡張機能タブで「Docker」を検索してインストールします。
Dev Containers、Remote Developmentなどを入れておきましょう。

## 何から始めるべきか
### 1．Githubのリポジトリを作る
GitHubのリポジトリから作るのが一番おすすめです。Pagesを作るなら"Github PageでBlogサイトを立ち上げる一番簡単な方法"を参考にしてください。
### 2. Vscodeの"ようこそ”から
VSCodeの”ようこそ”画面からGitリポジトリのクローンを実行しましょう。
まずは、ローカルにクローンを作成ましす。　(例　C:\work\リポジトリ名\...)
### 3. Dockerコンテナの作成
VsCodeからDockerコンテナを作成します。
画面左下の青い><マークから作成してください。　Pagesを作るなら、「Jekyll」Microsoftがおすすめです。

コマンドラインを使う方は、以下のコマンドを使用して新しいコンテナを作成します。
```bash
docker run -it --name my-container -v ${PWD}:/workspace -w /workspace ubuntu:latest /bin/bash
```
このコマンドは、`my-container`という名前のUbuntuコンテナを作成し、現在のディレクトリをコンテナ内の`/workspace`にマウントします。
ローカルのディレクトリと、Docker上のディレクトリは自動的にリンクされます。

### 4. コードのコミットとプッシュ
VsCodeのソース管理タブから、GitHubへコミットできます。 ※　メッセージは必ず入力しましょう。私の環境ではコミットが正常に終了しません。

コンテナ内で開発を行い、変更をGitHubにコミットしてプッシュします。以下のコマンドを使用して、変更をコミットし、リモートリポジトリにプッシュします。
コマンドラインを使いたい方はこちら
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

## まとめ

仮想環境と、ローカルにあるディレクトリの違い、ローカルリポジトリとリモートリポジトリの整合、各種あるDockerの連携方法等を、できる限りVsCodeのGUIで行うには、これが一番簡単かもしれません。

これで、Windows上でDockerコンテナを使用してVSCodeで開発し、そのコードをGitHubにコミットする基本的な手順が完了しました。DockerとVSCodeを連携させることで、効率的な開発環境を構築できます。お試しください！
