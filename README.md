# shigefuji.github.io 構築メモ
### こんな構成にしたい
様々な問題がある環境だが、これしかなかった。
※JekyllはWindowsを正式サポートしていない。
開発はWondowsPCで行い、ローカルのVSCodeでコードやMDファイルを書き、
GitHubのリポジトリにPostする。　
ローカルでもJekill が動いて確認できる事が必要で、GitHubPage上でも同じ表示になる事

https://jekyllrb.com/docs/installation/windows/#installation-via-bash-on-windows-10
winowsでのインストールお作法はここにあるが、色々エラー出て挫折・・ｗ
また、できる限りWindowsベースで開発したいので、DockerのJekill(Micorosoft)イメージを使わせてもらう

Githubにレポジトリ作成　→　ユーザー名.github.io  これ以外だとサブフォルダになる。(特別な名前)
　　　　　　　　　　　　　　README.mdだけを作っておく。
Vscodeで、pullする。ディレクトリが作成されるので、Dockerコンテナにリモート接続する
ローカルとDocker上のディレクトリがリンクされる。　

開発コンテナ接続後に、ターミナルからjekyll　new . を行う。

https://docs.github.com/ja/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll
詳しい情報はここにある。

VsCodeからGithubにコミット同期をすると、Web上でActionが動き公開される。
Githubでサポートされているテーマは、限られている。Jekyllのバージョン3.9

jekyllで最初に作成される、#theme: minimaとその他のテーマは構成が違うので注意
スタイル　home、postとかは無いので、　defaultに変更する事。

ローカルで動かすためには、GemFile、_config.ymlを変更する。




### 開発環境
OS　：　Winodws　10
仮想環境　：　WOL2（Ubuntu）+　Docker　(MicrosoftのJekyllイメージ)

### 注意事項
※　GitHubPages対応のため、Jekyllのバージョンは、正式対応に合わせる事！
※　
