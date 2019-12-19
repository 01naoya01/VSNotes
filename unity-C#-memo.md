---
tags:
    - Unity
---

if(Input.GetKey(KeyCode.Space)){
    //Aを押した時の動作
    //Input.GetKeyUpでキーから指から離れたら
    //Input.GetKeyDownでキーが押されたら
    //Input.GetKeyでキーが押されている間
}

transform.Translate(0f,0f,0f);  //移動を表す，(x,y,z)の座標に対して速さを設定できる

transform.position=new Vector3(0f,0f,0f);   //Tlanslateは移動だが，これは瞬間移動って感じで，その座標に移動できる

transform.Rotate(0f,0f,0f);     //X軸を中心に回転させる

Destroy(col.gameObject);    //Destroyはオブジェクトを消す，gameObjectは自分自身を指す

触れた相手のオブジェクトを消したかったらDestroy(col.gameObject);

void OnCollisionEnter(Collision col){
    //何かにぶつかった時のコードを書く
    if(col.gameObject.name=="Cube"){
        //ぶつかったオブジェクト名がCubeだった場合の動作をここに書く
    }
}

関数外でpublicで宣言すれば，変数の中身を変更する際，わざわざスクリプトを書き換える必要はなく，インスペクトから変数の中身を変更することができる
publicはGameObject等を定義してインスペクターから使いたいときでも必要になる．

using UnityEngine.UI;
//textを使う時に宣言する,Text型を使う時はpublicを使用する．
hierarchyのcreateでtextを生成する．位置はaltを押しながら9つの四角みたいなのをクリックすれば変更できる．
変数名.text=でテキスト型の変数の中身を変える．+でつなげて変数.ToString()で数字を文字に変えることができる．
スクリプトに入れたらunityに戻って，インスペクターのpublicした変数のところにnoneってなってるからtextオブジェクトをつっこめばok

Random.Range(乱数範囲の最小値,乱数範囲の最大値)
例えば1から6を出す時はRandom.Range(1,7)とかく，最大は+1しないといけない，勿論小数がいいならfをつける

下に落ちた時に元に戻すにはそのオブジェクトの座標で判定する．
transporm.position.xで，そのスクリプトを持ってるオブジェクトのx座標が返ってくる，比較する値には小数なのでfをつける

Time.fixedTimeでゲームが始まってからの時間を取得できる．ToString()をつけてtextに入れて表示させておけば時間をずっと表示させておくことができる．型はfloat型で入ってる．ToString()のカッコに"F1"と書けば小数点第一位まで表示するように固定できる，F2だったら第二位までって感じで調節できる

他のオブジェクトの情報をscriptから参照したい場合は例えばTransformを参照したいならTransformで宣言する．実際にどのオブジェクトの変数にしたいかは，textの時みたいにpublicにしてinspectorからつっこむ

Instantiate(gameObject型，Vector3型，Quaternion.identity));
これでクローンを作る，vector3型は，ここで直接指定するならnewした形を書く，Quaternion.identityは回転してないことを示す，gameObject型は，型をpublicで宣言したらインスペクターにつっこむ
例 Instantiate(sphere,new Vector3(0f,0f,0f),Quaternion.identity);
増やすもののオブジェクトがinstantiateを実行するスクリプトを持っていたらクローンがクローンを生み出すので注意，空のオブジェクト等にinstantiateのスクリプトを渡せばよい

角度を変えたいときはQuaternion.Euler(x,y,z)にすればよい
identityは(0f,0f,0f)と同じ


public Rigidbody rb;
rb.AddForce(x,y,z);
x,y,z方向に発射するって感じ．例えばxとyを100fにすればxとy軸の間みたいな方向に飛ばせる．これはRigidbodyでないと使えない．インスペクターのRigidbodyをrbにつっこむ．

transform.rotation=Quaternion.Euler(0f,0f,0f);
方向を変える

transform.localScale += new Vector3(0.01f,0.01f,0.01f);
大きさを変える

transform.localScale.x
で大きさを取得できる

Time.deltaTimeはUpdate関数が1ループしてレンダリング(描画)するまでの時間，Updateの1回の更新時間と考えてもいいと思う

using UnityEngine.SceneManagement;
これを上のところに入れたら下のLoadSceneを使える

SceneManager.LoadScene("シーンの名前");
変化後のシーンの名前を入れたら，そのシーンに変わる

void OnTriggerStay(Collider col){
    if(col.gameObject.name=="入った相手"){
        //処理
    }
}
触れてる間ずっとって感じの処理をする
