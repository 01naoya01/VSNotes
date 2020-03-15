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

# 降順でソートしたい場合

sort(v.begin(), v.end(),greater<int>());

とすればよい

# 2次元vectorを初期化してイテレータを使って列挙するソースコード

他にも2-7-Millipnaire等は参考になると思う

#include<iostream>
#include<algorithm>
#include<vector>
#include<stack>
#include<queue>
#include<string>
#include<utility>
#include<chrono>
#include<random>
#include<cstdio>
#include<set>
#include<map>
#define MAX_N 10
#define MAX_M 100
#define REP(i,n) for(int i=0;i<n;i++)
using namespace std;

void print2D(vector<vector<int > >& vec2){
    vector< vector< int> >::iterator it2;
    for( it2 = vec2.begin(); it2 != vec2.end(); it2++){
        vector< int>::iterator it1;
        for (it1 = (*it2).begin(); it1 != (*it2).end(); it1++){
            cout << *it1 << " ";
        }
        cout << endl;
    }
}

int main(){
    vector<vector<int>>a(4,vector<int>(3));
    a={
        {1,2,3},
        {2,3,4},
        {3,6,7},
        {1,7,9},
    };
    print2D(a);
}

# 小数の桁数を多くして出力したい場合

printf("%.8f\n",ans);

# 床関数 

floor(x)でx以下の最大の整数を得る
