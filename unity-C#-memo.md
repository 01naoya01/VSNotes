---
tags:
    - Unity
---

if(Input.GetKey(KeyCode.A)){
    //Aを押した時の動作
    //Input.GetKeyUpでキーから指から離れたら
    //Input.GetKeyDownでキーが押されたら
    //Input.GetKeyでキーが押されている間
}

transform.Translate(0f,0f,0f);  //移動を表す，(x,y,z)の座標に対して速さを設定できる

transform.position=new Vector3(0f,0f,0f);   //Tlanslateは移動だが，これは瞬間移動って感じで，その座標に移動できる

transform.Rotate(0f,0f,0f);     //X軸を中心に回転させる

Destroy(gameObject);    //Destroyはオブジェクトを消す，gameObjectは自分自身を指す

触れた相手のオブジェクトを消したかったらDestroy(col.gameObject);

void OnCollisionEnter(Collision col){
    //何かにぶつかった時のコードを書く
    if(col.gameObject.name=="Cube"){
        //ぶつかったオブジェクト名がCubeだった場合の動作をここに書く
    }
}

関数外でpublicで宣言すれば，変数の中身を変更する際，わざわざスクリプトを書き換える必要はなく，インスペクトから変数の中身を変更することができる

using UnityEngine.UI;
//textを使う時に宣言する,Text型を使う時はpublicを使用する．
変数名.text=でテキスト型の変数の中身を変える．+でつなげて変数.ToString()で数字を文字に変えることができる．
スクリプトに入れたらunityに戻って，インスペクターのpublicした変数のところにnoneってなってるからtextオブジェクトをつっこめばok

Random.Range(乱数範囲の最小値,乱数範囲の最大値)
例えば1から6を出す時はRandom.Range(1,7)とかく，最大は+1しないといけない，勿論小数がいいならfをつける

下に落ちた時に元に戻すにはそのオブジェクトの座標で判定する．
transporm.position.xで，そのスクリプトを持ってるオブジェクトのx座標が返ってくる，比較する値には小数なのでfをつける

Time.fixedTimeでゲームが始まってからの時間を取得できる．ToString()をつけてtextに入れて表示させておけば時間をずっと表示させておくことができる．型はfloat型で入ってる．

他のオブジェクトの情報をscriptから参照したい場合は例えばtransformを参照したいならtransformで宣言する．実際にどのオブジェクトの変数にしたいかは，textの時みたいにpublicにしてinspectorからつっこむ

Instantiate(gameObject型，Vector3型，Quaternion.identity));
これでクローンを作る，vector3型は，ここで直接指定するならnewした形を書く，Quaternion.identityは回転してないことを示す，gameObject型は，型をpublicで宣言したらインスペクターにつっこむ
例 Instantiate(sphere,new Vector3(0f,0f,0f),Quaternion.identity);
増やすもののオブジェクトがinstantiateを実行するスクリプトを持っていたらクローンがクローンを生み出すので注意，空のオブジェクト等にinstantiateのスクリプトを渡せばよい

角度を変えたいときはQuaternion.Euler(x,y,z)にすればよい
identityは(0f,0f,0f)と同じ





