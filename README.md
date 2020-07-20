*JapanCoin*
=====================================
![jcoin_nsis-header](https://user-images.githubusercontent.com/67356715/87230042-eed4b300-c3e7-11ea-8994-d648a194622c.png)

オフィシャルサイト：https://japancoin.jp

*JapanCoin*とは?
----------------
*JapanCoin*は、他の仮想通貨とは違い、暗号資産や送金などが目的では無く、「気持ち」を送るために利用される仮想コインとして使うために作成しております。

### *JapanCoin*の特徴

- プレマイニングは100JPC(それも何処行ったかわからない)
- 日本人が作成、GithubのREADMEもissuesも公式サイトも日本語
- 価値がないところに価値がある？

詳しくはオフィシャルサイトをご覧ください。

技術的な概要
----------------
LiteCoin Core v0.18.1を元に創られた仮想コインでアルゴリズムをはじめ技術的な仕様はほぼLiteCoinと同じです。

|項目 |内容 |
|:---|:---|
|名称 |JapanCoin |
|名称(日本語表記)	|ジャパンコイン |
|ティッカーコード及び単位 |JPC |
|最大供給量 |840,000,000 JPC |
|プレマイニング |100 JPC |
|主な利用目的 |「気持ち」の送信 |
|技術的なベース |Litecoin 0.18.1 |
|コンセンサス	|Proof of Work |
|アルゴリズム	|scrypt |
|SEGWIT	|対応 |
|Lightning Network |対応 |
|接続ポート |25366 |
|ブロック報酬	|50 JPC |
|ブロック報酬半減 |840,000ブロック毎 |

このプロジェクトの現状
----------------
**開発途上でまだ仕様も固まっているとは言えない段階ですので、今後発行済みブロックチェーンのリセットを含め仕様の変更があるかもしれません。**

テスト段階だと思ってください。間違ってもがっつりマイニングしてもなにもいいことがないとおもわれます。


利用の開始について
----------------
申し訳ありませんが、現在バイナリ形式での配布をしていませんので、お使いの環境に合わせてコンパイル、ビルドしていただく必要がございます。

※Windows64bit版のみバイナリ形式を用意しました。

基本的にLitecoinと同じようにコンパイルできるので分からないことがあればLitecoinについての情報が役に立つかと思います。

### Windows
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-windows.md  
をご覧ください(英語のままですみません)。

※**あまりにも面倒だと思う**ので一応コンパイル済みのバイナリをアップロードしておきます(64bit用です)。

[japancoin-20200712.zip](https://japancoin.jp/release/japancoin-20200712.zip)
bin フォルダに各実行ファイルが入っています。

**WSL(Windows Subsystem for Linux)が必要になるなど大変面倒で時間のかかるいばらの道です。**

WSLのセットアップについては別途お調べください。

私の場合は WSL2でUbunt18.04をで比較的すんなりビルド出来ました。

ただ WSL2を使ったせいかやたらとmakeに時間がかかりました。

### Linux
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-unix.md  
をご覧ください(英語のままですみません)。

#### Ubuntu/Linux mint

Ubunt16.04 より新しいUbuntuやLinux mintなどでは protocのバージョンが新しすぎるためかうまくmakeできません。
$ autogen.sh
を実行する前に
$ protoc --version
でprotocのバージョンを確認し、表示されるバージョンが 3.X.X など 2.6.X より新しい場合は、下記手順でprotocのバージョンを下げることができますが、環境に影響を及ぼす可能性がありますのでご注意ください。
~~~
$ sudo apt-get install -y libgcc1 gdebi
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/libprotoc-dev_2.6.1-1.3_amd64.deb
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/libprotoc9v5_2.6.1-1.3_amd64.deb
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/libprotobuf9v5_2.6.1-1.3_amd64.deb
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/libprotobuf-dev_2.6.1-1.3_amd64.deb
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/libprotobuf-lite9v5_2.6.1-1.3_amd64.deb
$ wget http://archive.ubuntu.com/ubuntu/pool/main/p/protobuf/protobuf-compiler_2.6.1-1.3_amd64.deb
$ sudo gdebi libprotobuf9v5_2.6.1-1.3_amd64.deb
$ sudo gdebi libprotoc9v5_2.6.1-1.3_amd64.deb
$ sudo apt remove libprotobuf-dev
# 念のため削除されるパッケージを確認してください。
$ sudo gdebi libprotobuf-lite9v5_2.6.1-1.3_amd64.deb
$ sudo gdebi libprotobuf-dev_2.6.1-1.3_amd64.deb
$ sudo gdebi libprotoc-dev_2.6.1-1.3_amd64.deb
$ sudo apt remove protobuf-compiler
$ sudo gdebi protobuf-compiler_2.6.1-1.3_amd64.deb
$ protoc --version
libprotoc 2.6.1
~~~

Ubuntu 16.04 での流れを簡易にまとめると以下のようになります。

~~~
$ sudo apt-get update
$ sudo apt-get install -y git build-essential libtool autotools-dev automake pkg-config bsdmainutils python3 libssl-dev libevent-dev libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libminiupnpc-dev libzmq3-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libqrencode-dev libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev libprotobuf-dev protobuf-compilersudo apt-get install -y build-essential libtool autotools-dev automake pkg-config bsdmainutils python3
$ git clone https://github.com/JapanCoinCenter/japancoin.git
$ cd japancoin
$ ./contrib/install_db4.sh `pwd`
# 上記コマンドで最後の方に表示される `export ~' を実行すある
# ↓例
# $ export BDB_PREFIX='/home/mydir/japancoin/db4'
$ ./autogen.sh
$ ./configure BDB_LIBS="-L${BDB_PREFIX}/lib -ldb_cxx-4.8" BDB_CFLAGS="-I${BDB_PREFIX}/include"
# もしVPS等でメモリが1.5G未満など極端に少ない場合は以下のようにCXXFLAGSオプションを使用する
# $ ./configure BDB_LIBS="-L${BDB_PREFIX}/lib -ldb_cxx-4.8" BDB_CFLAGS="-I${BDB_PREFIX}/include" CXXFLAGS="--param ggc-min-expand=1 --param ggc-min-heapsize=32768"
$ make
$ makeはそこそこ時間がかかります(30分以上?)。
$ sudo make install
~~~
#### CentOS
CentOS 8 での流れを簡易にまとめると以下のようになります。  
※GUI無しでコンパイルした時の手順です。
※sudoを許可したユーザーでの作業例です。
~~~
$ sudo dnf install gcc-c++ libtool make autoconf automake openssl-devel libevent-devel boost-devel
$ git clone https://github.com/JapanCoinCenter/japancoin.git
$ cd japancoin
$ JAPANCOIN_ROOT=$(pwd)
$ BDB_PREFIX="${JAPANCOIN_ROOT}/db4"
$ mkdir -p $BDB_PREFIX
$ wget 'http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz'
$ tar -xzvf db-4.8.30.NC.tar.gz 
$ chmod u+w db-4.8.30.NC/dbinc/atomic.h
$ vi db-4.8.30.NC/dbinc/atomic.h
# japancoin/db-4.8.30.NC/dbinc/atomic.h を修正(読み込み専用になっている)
147行目と179 行目の
__atomic_compare_exchange
を
__atomic_compare_exchange_db
に書き換える
$ cd db-4.8.30.NC/build_unix/
$ ../dist/configure --enable-cxx --disable-shared --with-pic --prefix=$BDB_PREFIX
$ make install
$ cd $JAPANCOIN_ROOT
$ ./autogen.sh
$ ./configure LDFLAGS="-L${BDB_PREFIX}/lib/" CPPFLAGS="-I${BDB_PREFIX}/include/"  --without-gui
$ make
$ sudo make install
~~~

### macOS
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-osx.md  
をご覧ください(英語のままですみません)。

すみません、まだmacOS上でテストしていません。そのうちやります。

マイニングについて
----------------
![mining-2648004_620](https://user-images.githubusercontent.com/67356715/87242136-f2f2e600-c464-11ea-9bce-074a5b80ce08.png)

***JapanCoin*** **は全く資産価値のないコインですので発掘難易度がとても低く簡単にマイニングが可能です**。

Bitcoinや一般的なオルトコインだとソロマイニングだと現実的ではありませんが、JapanCoinは容易に発掘が可能です。

基本的にLitecoinと同じアルゴリズムですのでLitecoinと同じようにcpuminer, ccminer, cgminerなどでマイニングすることも可能ですがこのプログラム単体でもマイニング可能です。

japancoind を下記のようにdeprecatedrpcオプションをつけて起動し、

```$ japancoind -deprecatedrpc=generate```

japancoin-cliで下記のようにすると1ブロックマイニングすることができます。成功すると生成されたハッシュが表示されます。失敗した場合は[]だけが表示されます。

```$ japancoin-cli generate 1```

現在、試験的にマイニングを行っておりますが、難易度に非常にむらがあるもののタイミングによっては上記方法でもマイニング可能だと思われます(2020年7月上旬時点)。

マイニング難易度が低いこと以外は一般的なオルトコインと同じですので、cgminerなどのマイニング用プログラムでのマイニング興味があるかたはそれぞれ適当にググって調べてください。
※やっつけですみません、余裕ができればもう少し導入しやすい説明文を書きます。

ところで、現在の発掘報酬は1ブロック当たり50JPCですが、50JPCもあれば充分だと思います。繰り返しになりますがこのコインはがっつりマイニングしておいて上場したときに売却益を狙う類のコインではありません(電気代の無駄です)。

開発者もJapanCoinを対して持っていないので開発者からしても上場するメリットはなく上場される可能性は限りなくなと思われます。

そもそも**仕様変更などでリセットする可能性がある**のでご留意下さい。

お金や物を渡すほどではないけどありがとうと思ったときに感謝の気持ちをなんとなく伝えるために送るのを想定しているので、1mJPCずつ送るなら50JPCでなん万回も送れちゃいます。

### マイニングプール

現在下記マイニングプールが公開されております。

http://pool.japancoin.center/

一般的なマイニングソフトウェアで設定する際のパラメータは下記のようになります。

- URL : stratum+tcp://pool.japancoin.center:3333
- アルゴリズム : scrypt
- ユーザー名 : 報酬受取に使用したい*JapanCoin*のアドレス
- パスワード : 適当な文字列

このマイニングプールでは、2％の手数料が取られます。また、発掘後100ブロック*JapanCoin*が発掘されてから承認され報酬が送られます。