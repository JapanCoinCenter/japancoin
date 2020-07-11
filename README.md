*JapanCoin*
=====================================
![jcoin_nsis-header](https://user-images.githubusercontent.com/67356715/87230042-eed4b300-c3e7-11ea-8994-d648a194622c.png)

オフィシャルサイト：https://japancoin.jp

*JapanCoin*とは?
----------------
*JapanCoinは*、他の仮想通貨とは違い、暗号資産や送金などが目的では無く、「気持ち」を送るために利用される仮想コインとして使うために作成しております(2020夏頃公開予定)。

詳しくはオフィシャルサイトをご覧ください。

技術的な概要
----------------
LiteCoin Core v0.18.1を元に創られた仮想コインでアルゴリズムをはじめ技術的な仕様はほぼLiteCoinと同じです。

このプロジェクトの現状
----------------
開発途上でまだ仕様も固まっているとは言えない段階ですので、今後発行済みブロックチェーンのリセットを含め仕様の変更があるかもしれません。

テスト段階だと思ってください。間違ってもがっつりマイニングしてもなにもいいことがないとおもわれます。

マイニングについて
----------------
***JapanCoin*** **は全く資産価値のないコインですので発掘難易度がとても低く簡単にマイニングが可能です**。

Bitcoinや一般的なオルトコインだとソロマイニングだと現実的ではありませんが、JapanCoinは容易に発掘が可能です。

基本的にLitecoinと同じアルゴリズムですのでLitecoinと同じようにcpuminer, ccminer, cgminerなどでマイニングすることも可能ですがこのプログラム単体でもマイニング可能です。

japancoind を下記のようにdeprecatedrpcオプションをつけて起動し、

```$ japancoind -deprecatedrpc=generate```

japancoin-cliで下記のようにすると1ブロックマイニングすることができます。成功すると生成されたハッシュが表示されます。失敗した場合は[]だけが表示されます。

```$ japancoin-cli generate 1```

現在、試験的にマイニングを行っておりますが、難易度に非常にムラがあるもののタイミングによっては上記方法でもマイニング可能だと思われます(2020年7月上旬時点)。

マイニング難易度が低いこと以外は一般的なオルトコインと同じですので、cgminerなどのマイニング用プログラムでのマイニング興味があるかたはそれぞれ適当にググって調べてください。
※やっつけですみません、余裕ができればもう少し導入しやすい説明文を書きます。

ところで、現在の発掘報酬は1ブロック当たり50JPCですが、50JPCもあれば充分だと思います。繰り返しになりますがこのコインはがっつりマイニングしておいて上場したときに売却益を狙う類のコインではありません。

お金や物を渡すほどではないけどありがとうと思ったときに感謝の気持ちをなんとなく伝えるために送るのを想定しているので、1mJPCずつ送るなら50JPCでなん万回も送れちゃいます。

利用の開始について
----------------
申し訳ありませんが、現在バイナリ形式での配布をしていませんので、お使いの環境に合わせてコンパイル、ビルドしていただく必要がございます。

基本的にLitecoinと同じようにコンパイルできるので分からないことがあればLitecoinについての情報が役に立つかと思います。

### Windows
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-windows.md  
をご覧ください(英語のままですみません)。

※**あまりにも面倒だと思う**ので一応コンパイル済みのバイナリをアップロードしておきます(64bit用です)。

[japancoin-20200712.zip](https://japancoin.jp/release/japancoin-20200712.zip)

**WSL(Windows Subsystem for Linux)が必要になるなど大変面倒で時間のかかるいばらの道です。**

WSLのセットアップについては別途お調べください。

私の場合は WSL2でUbunt18.04をで比較的すんなりビルド出来ました。

ただ WSL2を使ったせいかやたらとmakeに時間がかかりました。

### Linux
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-unix.md  
をご覧ください(英語のままですみません)。

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

Ubuntu 16.04での流れを簡易にまとめると以下のようになります。

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

### macOS
詳しくは 　
https://github.com/JapanCoinCenter/japancoin/blob/master/doc/build-osx.md  
をご覧ください(英語のままですみません)。

すみません、まだmacOS上でテストしていません。そのうちやります。