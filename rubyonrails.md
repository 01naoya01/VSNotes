rails new sample_app
でsample_appというアプリを作る

rails s
で実行

rails generate controller home top
新しいWebページが自動で作られ、「localhost:3000/home/top」というURLにアクセスできるようになる
1. app/viewフォルダの中にhomeフォルダとtop.html.erbファイルが作成される
ビューとは、ページの「見た目」を作るためのHTMLファイルで，Railsからviewフォルダのviewが返されてページが表示されるって感じ
<image src="./rails/view.png">
厳密にいうと，Railsの中でcontrollerを経由してviewをブラウザに返す
<image src="./rails/controller.png">

2. home_controller.rbというファイルが作成されてtopメソッドが追加される
コントローラ内のメソッドをアクションと呼ぶ
コントローラ内のアクションは、ブラウザに返すビューをviewsフォルダの中から見つけ出す役割を担っています。具体的には、アクションは、コントローラと同じ名前のビューフォルダから、アクションと同じ名前のHTMLファイルを探してブラウザに返します。
<image src="./rails/アクション.png">

3. Rails内ではコントローラを経由してビューを返していますが、ブラウザとコントローラを繋ぐ役割を担うのがルーティングです。
ページが表示されるまでに、ルーティング→コントローラ→ビューという順で処理が行われていることを理解しておきましょう。
 <image src="./rails/routing.png">
 ルーティングは「config/routes.rb」に定義され、右の図のように
「get "URL" => "コントローラー名#アクション名"」という文法で
書かれます。
ブラウザから「localhost:3000/home/top」というURLが
送信されたときに、homeコントローラーのtopアクションで処理される

4. ページ作成のコマンドは「rails generate controller コントローラ名 アクション名」という意味である
同じ名前のコントローラがすでにある場合は、このコマンドを使うことはできません
 <image src="./rails/ページ作成コマンド.png">

5. CSSファイルは「app/assets/stylesheets」フォルダに入っています。
「rails generate controller home ...」コマンドを実行したときに、
CSSファイル(home.scss)も自動生成されます。
「scss」はCSSを拡張したもので、CSSを効率的に書く文法も使用できますが、このレッスンではCSSの文法のみを用いていきます。

Railsでは、「stylesheets」フォルダの中に保存されているCSSファイルに
コードを書けば、すべてのビューにCSSが適用されます。
 <image src="./rails/css.png">

6. 画像は、「public」フォルダに配置しておくと、「\<img src="/画像名" >」や「background-image: url("/画像名");」のように、画像名を指定するだけで、簡単に画像を表示することができます。
 <image src="./rails/画像フォルダ.png">
  <image src="./rails/画像指定.png">

7. リンクを作成するためには、\<a>タグでテキストを囲み、「href=" "」の中にURLを指定する必要があったことを思い出しましょう。
hrefの中身をルーティングのURL部分と同じにすることで、簡単にリンク先を指定することができます。
 <image src="./rails/リンク1.png"> <image src="./rails/リンク2.png">

8. index.html.erbのようなerbという形式のファイルでは、以下の図のように<% %>で囲むことで、HTMLファイルの中にRubyのコードを記述することができます。「erb」とは「Embedded Ruby（埋め込みRuby）」の略です。

<image src="./rails/erb1.png">

埋め込むRubyコードをブラウザに表示したい場合には、以下の図のように
<% %>ではなく、<%= %>を用います。

<image src="./rails/erb2.png">

これを使って，erb内で変数定義もできるが，これはアクション(controllerのメソッド)で定義するのが普通

<image src="./rails/処理の流れ.png">

通常、アクションで定義した変数をビューで使用することはできません。
しかし、変数名を「@」から始めることでこの変数は特殊な変数となり、ビューファイルでも使用することができます。
ですので、アクションで定義したビュー用の変数には「@」をつけ忘れないようにしましょう。

9. 縦の列のことを「カラム」、1行ずつのデータのことを「レコード」と呼ぶ
<image src="./rails/db1.png">

まずは、マイグレーションファイルと呼ばれる、データベースに変更を指示するためのファイルを作成しましょう。右の図のようなpostsテーブルを作成するマイグレーションファイルは「rails g model Post content:text」というコマンドで作成することができます。

<image src="./rails/migration.png">

先ほどのコマンドを実行すると、下の図のようにdb/migrateフォルダの下にマイグレーションファイルが作成されます。
<image src="./rails/migrationFile.png">

10. 「rails db:migrate」でマイグレーションファイルに書いてある指示通りにテーブルを作ってくれる
Railsでは、データベースに反映されていないマイグレーションファイルが存在する状態で、どこかのページにアクセスすると以下のようなマイグレーションエラーが発生してしまいます。そのため、マイグレーションファイルを作成した場合は必ず「rails db:migrate」を実行する必要があります。

11. さっき実行したrails g modelコマンドでPostモデルが定義されたファイルpost.rbがapp/modelsに作成されてる．ApplicationRecordを継承したクラスをモデルと呼ぶ．

「rails g model Post ...」の「Post」の部分には、実はモデル名を指定します。
<image src="./rails/model_name.png">
そして、このコマンドによって、以下の2つのファイルが作成されます。

* app/modelsフォルダにモデルが定義されたファイル
* db/migrateフォルダにマイグレーションファイル
<image src="./rails/railsgmodel.png">

作成されるpostsテーブルはこんな感じ
<image src="./rails/table.png">

12. 「rails console」という Ruby のコードを手軽に実行できる環境に入れる
「rails console」を使って、Postモデル（Postクラス）からPostインスタンスを作成しましょう。インスタンスを作成するにはnewメソッドを使います。
<image src="./rails/dbnew.png">
<image src="./rails/dbnew2.gif">

13. 作成したPostインスタンスをpostsテーブルに保存するには、saveメソッドを使います。saveメソッドを使うことができるのはPostモデルがApplicationRecordを継承しているためです。
<image src="./rails/db3.png">
<image src="./rails/db4.gif">

14. 「Post.first」とすることで、 posts テーブルにある最初のデータを取得することができる
<image src="./rails/postFirst.png">
「post.content」とすることで「Post.first」で取得したデータから投稿内容を取得することができる
<image src="./rails/postContent.png">
テーブルに保存されている全てのデータを取得するには、右の図のように「Post.all」を使う
<image src="./rails/postAll.png">
<image src="./rails/postAll[0].png">
<image src="./rails/postAll[0]content.png">

15. Railsでは、「views/layouts/application.html.erb」に共通のHTMLを書いておくことができる
application.html.erbの<%= yield %>についてだが，各ビューファイルはこの<%= yield %>の部分に代入され，application.html.erbの一部としてブラウザに表示されていた．
<image src="./rails/yield.png">
<image src="./rails/yield2.png">

16. では、最後に投稿一覧ページへのリンクを追加しよう。Rails ではlink_toというメソッドを使うと\<a>タグを作成することができるぞ。 link_to メソッドは Ruby のコードなので、「<%=%>」で囲むことに注意するのじゃ。
右の図のように、第一引数に表示する文字を、第二引数に URLを書くことでリンクが作成されるぞ。
<image src="./rails/link_to.png">

















<image src="./rails/.png">