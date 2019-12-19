---
tags:
    - VSnote
---

# VSnoteの使い方

[Qiita VSnoteについて](https://qiita.com/shizuma/items/8616bbe3ebe8ab0b6ca1)

2-5の隣接リストの実現方法2の構造体でなぜポインタが必要になるのかが分からない．

# 構造体のソートの仕方
2-5-Kruskalなどでも使っている

以下のURLでいうと，比較関数を使ったソートの仕方が一番手っ取り早い気がする．

https://qiita.com/a4rcvv/items/7cd217cc5fafef700dff

# ソートする際の注意

例えば

#define MAX_N 100

vector<int>e(MAX_N);

sort(e.begin(),e.end());

とすると，MAX_Nまで全部ソートしてしまう．ソートしたい範囲がVまでだとしても，MAX_NよりVの方が小さいので，ソートした結果，Vまでのところに0ばっかりが入ってしまうかもしれない．

なので以下のようにソートする範囲を指定してあげないといけない．

sort(e.begin(),e.begin()+V);

これでeの最初からVまでの部分をソートできる．

MAX_Nは10^8までなら余裕，10^9は恐らく1024MB下回る，10^10は間違いなく無理