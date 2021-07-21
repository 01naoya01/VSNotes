---
tags:
    - AndroidStudio
---

# 起動方法
windows10側でXlaunchを起動する
ここで，Disable access controlにチェックをつける
これによりVcXsrvが起動される

wslの/opt/android-studio/binで
sh studio.sh
を実行する



もしXサーバー関連のエラーが出たら以下を実行
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0.0

つまり\\wsl$\Ubuntu\home\naoyaのbashrcにこのコマンドが書かれてればよい

このコマンドで追加できる
echo 'export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0.0' >> ~/.bashrc

