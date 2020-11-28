# aptの更新
sudo apt update

sudo apt upgrade

sudo apt-get remove

# VScodeの開き方

code server1.go
で開く

もし保存できない場合はserver1.goに対して
sudo chmod 777 server1.go

# ローカルなwebアプリの開き方
goのプログラムからwebサイト開くには
go run server1.go

して、ブラウザから
localhost:8080

# apache2の起動再起動停止確認

sudo service apache2 restart

sudo service apache2 start

sudo service apache2 stop

sudo service apache2 status

# パッケージ一覧表示
sudo dpkg -l

# パッケージの場所
dpkg -L パッケージ名

# ファイアーウォールの起動・設定確認
sudo ufw enable

sudo ufw status

# go
バージョン確認
go version

goサーバー起動
go run server1.go

# パス通す
export PATH=$PATH:/usr/lib/go-1.14/bin

パスの確認
echo $PATH

goのgithub経由で何かをダウンロードした時のパス
\\wsl$\Ubuntu\home\naoya\go\src\github.com

消えない環境変数を設定するには
\\wsl$\Ubuntu\home\naoyaの.bashrcか.profileのどっちかにexport PATH=$PATH:/usr/lib/go-1.14/binを書けばいいらしい、goの場合両方書けばいけた、どっちが反応してるかは特に検証してない
https://qiita.com/yakumomutsuki/items/d2fd9f103df7f728c20b

# ipアドレス関連
ip address show　か　ifconfigを使えばwslに関するIPアドレスが分かる？

cmdでipconfigを使えばローカルIPに関してはwindowsの方もwslの方も分かる

ポートフォワーディング方法
https://qiita.com/yabeenico/items/15532c703974dc40a7f5
管理者権限でcmdで以下を実行

netsh.exe interface portproxy delete v4tov4 listenport=22
とすれば削除できる

netsh interface portproxy add v4tov4 listenport=80 listenaddress=192.168.11.4 connectport=80 connectaddress=192.168.98.113

netsh interface portproxy add v4tov4 listenport=22 listenaddress=192.168.11.4 connectport=22 connectaddress=192.168.98.113

確認方法は
netsh.exe interface portproxy show v4tov4

# go runでポート競合した場合
8080について確認したい時
sudo lsof -i:8080

ポートを消したい時？
sudo kill -9 PID

# 再ログイン(ubuntuの？)
exec $SHELL -l

# Vue.jsの環境構築
https://sabatoragamer.net/programing/vue-js/post-668/

# git
https://www.atmarkit.co.jp/ait/articles/2005/21/news023.html
https://note.nkmk.me/git-add-u-a-period/
http://www.aise.ics.saitama-u.ac.jp/~gotoh/IntroGitOnLinux.html

pushの流れ
ローカルリポジトリのフォルダの中に入る
1個だけaddしたいなら
git add ファイル名
バージョン管理されていて変更があった全てのファイルがadd
バージョン管理されていないファイルとか新しく作られたファイルはaddされない
git add -u
変更されたファイル、削除されたファイル、新しく作られたファイル、全部addされる
git add -A
カレントディレクトリ以下の変更があったもの全てをadd
git add .


git commit -m "コメント"
git push
あるいは
git push -u origin main
これはoriginというリモートリポジトリのmainというブランチにpushしていることを表す。
git push -u origin master
でいけるらしいが俺は無理

-uについては以下を参照
https://qiita.com/shumpeism/items/1b8027c8905ca826416d
