|用語|意味|
| ---- | ---- |
| gem | パッケージ、ライブラリーのこと |
|bundler|gemを管理するgem|
|Gemfile|そのrailsアプリで使うgemの一覧を管理するファイル、新しくgemを追加したい時はこのファイルに追記する|
|Gemfile.lock|実際にそのrailsアプリにインストールされてるgemの一覧|
|gem 'rails', '>= 6.0.3'|6.0.3以上の最新のバージョンがインストールされる|
|gem 'rails', '~> 6.0.3'|6.0.3以上で6.1.0未満の最新バージョンがインストールされる|
|bundle install|gemをインストールするw|
|githubのcommitのコメントは過去形じゃなくて現在形や命令系等を使う||
|bundle install --without production|本番用以外のgemをインストールする.productionは本番環境で使うものを示してる。ローカル開発環境にこれが入っててもしょうがないので。一旦ローカル環境で実行させるのは、Gemfile.lockに変更を反映させないと本番環境で上手くいかないから|
|heroku login||
|heroku create|herokuの新しいアプリケーションを作成|
|git push heroku master|herokuにデプロイ|
|has_many :microposts|バリデーションの一つ。1つのインスタンスに対して複数のmicropostsモデルがある|
|belongs_to :user|バリデーションの一つ。1つのインスタンス(このバリデーションを書いてるモデルのデータ1つ)に対して1つのuserモデルにのみ属することを意味する|
|validates :content, presence: true|バリデーションの一つ。この場合、contentに空の入力があったらエラーを吐く|
|validates :content, length: { maximum: 140 }|バリデーションの一つ。contentの長さの最大を140に設定する|
|rails generate model User nama:string email:string|モデルの生成|
|rails generate controller StaticPages home help|コントローラの生成|
|rails destroy controller StaticPages|削除|
|rails db:rollback|1つ前の状態に戻す|
|rails db:migrate VERSION=0|最初の状態に戻す。数字を帰れば指定したバージョンに戻せる|
|テンプレート|Railsでは、テンプレートとはすなわち「ビュー」を指す。|
|assert_response :success|HTTPステータスが:success(つまり200)なら成功|
|assert_select "title", "Home | Ruby on Rails Tutorial Sample App"|特定のHTMLタグが存在するかどうかをテストする。この場合、＜title>タグ内にHome | Ruby on Rails Tutorial Sample Appという文字列があるかどうかをチェックする。|
|setupメソッド|テストファイル上で記載するメソッドで、各テストが走る前に実行されるメソッド。|
|<% ... %>|中に書かれたコードを単に実行するだけで何も出力しません|
|<%= ... %>|中のコードの実行結果がテンプレートのその部分に挿入されます|
|provide(:title, "Home") と yield(:title)|provide(:title, "Home")で:titleというラベルに"Home"を関連付けて、yieldで呼び出す|
|テスト駆動開発（TDD）|「 red ・ green ・REFACTOR」サイクルを繰り返す|
|minitest-reporters|red や green の表示を見やすくするgem。/test/test_helper.rbに追記することで使えるようになる。|
|bundle exec guard init|guardを初期化し、Guardfileを生成|
|bundle exec guard|guardを起動|
|bin/spring stop|guardのテストが原因不明で動かなくなったらこのコマンドを実行。Spring（Railsの情報を事前読み込みしてテストを高速化するツール）を止めて再起動する。|
|_pathと _url|_pathはルート以下の文字列を返す。urlは完全なURLの文字列を返す。help_pathなら'/help'、help_urlなら'https://www.example.com/help'|
|rails routes|コマンド、HTTPリクエストの種類も含めて、routeを全て表示してくれる.|
|""と''の違い|""は式展開できるが、''はできない。""の場合は#のような特殊な文字を使う時はバックスラッシュを前に付ける。''の場合はそのまま使えるが前にバックスラッシュが付く。|
|.to_s|変数.to_sで変数の中身を文字列に変換する|
|.nil|変数.nil?で、変数がnilかどうかを返す|
|puts "The string '#{foo}' is nonempty." unless foo.empty?|unlessの説明で、unlessの後がfalseなら前文のputsが実行される|
|falseとnil|Rubyのオブジェクトのうち、オブジェクトそのものの論理値がfalseになるのは、false自身とnilの2つしかなく、「!!」（「バンバン（bang bang）」と読みます）という演算子を使うと、そのオブジェクトを2回否定することになるので、どんなオブジェクトも強制的に論理値に変換できます。|
|rubyのメソッド呼び出し時の引数|引数を省略すればデフォルト値が適用されるが、引数を渡す際に、カッコを省略することができる。例えばstring_message()というメソッドがあったとすると、string_message foo みたいな感じでで空白あけるだけで引数を指定することができる|
|暗黙の戻り値|メソッド内で最後に評価された式の値が自動的にreturnされる|
|helpersフォルダのメソッドがビュー側で使える理由|rubyならincludeメソッドを使ってモジュールを読み込むが、railsでは自動的にヘルパーモジュールを読み込むのでわざわざinclude行を書く必要はない|
|.split|文字列を空白区切りで配列にする。.split('x')とかにしたらx区切りになる|
|.first,.second,.last|.lastで最後の配列を示す。これは[-1]と同じ|
|.include?(42)|配列に42という要素があったらtrue|
|.shuffle|配列の中身をシャッフルしたものを返す。元の配列の中身は変わらない。.shuffle! にすると元の中身が変わる|
|.sample|配列の要素をランダムに1つ取ってくる。.sample(2)なら2つ取ってくる|
|.push(6),<< 6|配列の末尾に6を追加する。a<<5<<"aa"とかなら連続で5とaaを追加する。なお、rubyでは異なる型が配列の中で共存できる。|
|.join|配列を単純に連結する。.join(',')で、','で連結する|
|範囲(range)|0..9とかで0123456789を示せる。例えば(0..9).to_aで[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]に変換できるし、a[0..2]で、配列aのindexの0 1 2を取り出して["foo", "bar", "baz"]みたいにすることができる。文字列に対しても使えて、('a'..'e').to_aってしたらabcdeまでの配列が作れるし、a[2..-1]にしたらa[2..(a.length-1)]と同じ使い方ができる。因みに-7とかなら後ろから7番目の要素を出せる。|
|(1..5).each { |i| puts 2 * i }|each doによるfor文の実行する行が1行だけならこういう風にブロックを使って記述することもできる|
|3.times { puts "Betelgeuse!" }|3回ブロックを実行できる|
|%w[a b c]|%wで文字列の配列を作成する|
|%w[a b c].map { |char| char.upcase }|["A", "B", "C"]を返す。mapメソッドは、渡されたブロックを配列や範囲オブジェクトの各要素に対して適用し、その結果を返す。|
|%w[A B C].map(&:downcase)|symbol-to-procという記法で、上のやつの省略形|
|('a'..'z').to_a.shuffle[0..7].join|これは復習。これはaからzの中からランダムに8つ取って連結して1つの文字列にして返す。|
|user = {}|これはハッシュの空を表し、ブロックとは全くの別物。紛らわしい。ハッシュは配列と違って並び順が保証されない。|
|シンボルと文字列の違い|文字列を比較するときは1文字ずつ比較していくが、シンボルの場合は1度に全体を比較できるらしい.あとシンボルは文字列みたいにsplitとかreverseとかは使えないし、:foo-barとか:2fooは無理、どんな文字もシンボルにできるわけではない。|
|{:user=>{:name=>"Michael Hartl", :email=>"mhartl@example.com"}}|こういう風にハッシュの中にハッシュがある場合はparams[:user][:email]っていう感じで使うことができる。|
|puts "a", 7|カンマで区切れば2連続でputsできる|
|.inspect|inspectはオブジェクトや配列をわかりやすい文字列にして返すメソッド|
|p :name|puts :name.inspect と等価|
|stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload'|stylesheet_link_tagというメソッドを呼び出してる。メソッドを呼ぶ時にかっこを省略することができる。そして引数は2つで1つは'application'でもう一つはハッシュである。ハッシュが最後の引数の場合にのみ{}を省略することができる。|
|HTMLソースで生成される16進数|これらはRailsによって挿入されているもので、サーバー側で変更が発生した場合にブラウザがCSSを再読み込みするのに使います。この16進文字は、互いに重複しない仕様になっている|
|mediaタイプ|そのスタイルをどのメディアに適用するかを決める。例えばallならなんでもだし、printならプリンタ、screenならパソコン、handheldなら携帯電話になる|
|s = String.new("foobar")|s = "foobar"と等価。省略してるだけで、実際はStringクラスのインスタンスを生成してコンストラクタで初期化してる|
|a = Array.new([1, 3, 2])|Stringと同様|
|h = Hash.new|ハッシュはStringやArrayと違い、デフォルト値を引数に取る。引数を与えない場合はnilになる。例えばh = Hash.new(0)なら、h[:foo]等の存在しないキーを調べると0が返ってくる。デフォルトならnilが返ってくる|
|クラスメソッド|クラスの中のメソッド名を付ける時にself.additionみたいにself.を付けたらクラスメソッドになる。クラスメソッドはインスタンスから呼び出すんじゃなくてクラス自体に対して呼び出す時に使う。例えばUser.newでインスタンスを生成してるけど、実際.newはインスタンスに対して呼び出すんじゃなくてクラス自体に対して呼び出してる。こういうのがクラスメソッド|
|インスタンスメソッド|クラスメソッド以外の、クラスの中に定義されてるメソッドは全部インスタンスメソッド。これはインスタンスに対して呼び出すもので、additionというメソッドがあったとして、User.additionとかは無理、User.newしたインスタンスに対して、a.additionみたいな感じで使うことができる。|
|.class|変数.classで、変数のクラスを調べる|
|.superclass|変数.class.superclassで、変数のクラスのスーパークラスを調べる。変数.class.superclass.superclassで更に上を調べれる|
|Rubyのオブジェクト|スーパークラスを辿っていくと、全てがオブジェクトである。|
|リスト4.15の話|引数で文字列を取るメソッドを使うためにクラスを作るならStringクラスを継承するのが自然、そうすればメソッドでself(インスタンス自身)を使ってメソッドを実装できる。なお、Stringを継承したクラスなので、Stringにあるメソッドを使う時はself.reverseみたいな感じでselfを付ける必要はない。|
|組み込みクラスの変更|組み込みの基本クラスを拡張できる。例えばclass Stringと定義して、新しくメソッドを追加すれば、String型の変数に対して追加したメソッドを使える。けどこれは真に正当な理由がない限り無作法なことであると考えられている。|
|.blank?|その変数がスペースや他の空白文字を除いて空だったらtrue、つまり"    ".empty?はfalseだが、"     ".blank?はtrueで、nil.blank?もtrueになる。因みにnil.empty?はエラーを吐く|
|コントローラ内のインスタンス変数|Railsでは、インスタンス変数をコントローラ内で宣言するだけでビューで使えるようになる。|
|attr_accessor :name, :email|ユーザー名とメールアドレス（属性: attribute）に対応するアクセサー（accessor） をそれぞれ作成します。アクセサーを作成すると、そのデータを取り出すメソッド（getter）と、データに代入するメソッド（setter）をそれぞれ定義してくれます。具体的には、この行を実行したことにより、インスタンス変数@nameとインスタンス変数@emailにアクセスするためのメソッドが用意されます。逆に言うと普通に定義した変数はクラス外で使えない。attr_accessorを使ってるからgetterとsetterを用意してくれてインスタンスで使えるようになる。|
|initializeメソッド|コンストラクタになる。インスタンス生成時に実行される。|
|マスアサインメント（mass assignment）|引数で、最後のハッシュ引数の波カッコは省略できることを利用して、メソッドを呼び出す時に()に渡す引数を{}なしで書く手法？一般的には別の意味があるっぽい？分からん。|
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
