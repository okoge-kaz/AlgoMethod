# AlgoMethod

## C++ Environments

### Compile Options

[C++ compile options](https://triple-four.hatenablog.com/entry/20210623/1624458051#-Wshadow--%E3%82%B7%E3%83%A3%E3%83%89%E3%82%A6%E3%82%A4%E3%83%B3%E3%82%B0%E3%82%92%E8%AD%A6%E5%91%8A)

- `-Wall`

  以下の複数の警告を有効にするオプション

  - `-Wuninitialized`

    初期化していない変数を使用した場合に警告を出すオプション、Competitive Programming において、ゼロ初期化をしていないことなどによるミスを事前に防ぐことができる。

  - `-Wparenthes`

    if 文や while 文における `()`のなかで `=`代入が行われている場合などに警告を表示してくれる。

- `-Wextra`

  - `-Wsign-compare`

    符号なし整数(`unsigned int`, `unsigned long`)と、符号付き整数(`int`, `long`)を比較する場合に警告を出すオプション

- `-Wshadow`

  変数名が同じスコープ内で再定義されている場合に警告を出すオプション

  ２重定義されていることで意図せむ代入がされている場合に気づくことができる。

- `-Wfloat-equal`

  浮動小数点型での `==`, `!=`を検出するオプション

  丸め込み誤差、情報落ち、桁落ちなどに起因する想定外の挙動を防止することができる。

  本来的には、`fabs(a - b) < 1e-10`のように EPS を設定して比較することが望ましい。

- `-Wno-char-subscripts`

  競技プログラミングに限らず、ライブラリに頼らずに文字列を扱う場合に、文字列の添字に文字を指定することがある。
  そのため、`-Wall`で有効になる配列の添字に`char`型を用いることを警告するオプションを無効にすることが有効なときがある。
  ただし、明示的な型変換を行えば、このオプションを有効する必要はない。

[Compiler Option 一覧](http://solid.kmckk.com/doc/skit/current/solid_toolchain/overview.html#cmdoption-W-warning)にもあるように `-Wall -Wextra`で有効化される警告はかなりの数があるので、すべてを記載することはしない。

有効化されるオプション一覧については、GCC のものだが[ここ](https://gcc.gnu.org/onlinedocs/gcc-9.3.0/gcc/Warning-Options.html#index-Wparenthes)にある。


実行時チェックに関するコンパイルオプション

- `-ftrapv`

  オーバーフローの検出

  符号付き整数型の加算・減算・乗算時にオーバーフローを検知するトラップを生成します。 オーバーフローが発生するとトラップに引っかかり、即座にプログラムが終了します。
  競技プログラミングにおいては、しばしば、オーバーフロー関連のひっかけ問題を見かけるので役立つ

- `-fstack-protector-all`

  ローカル変数の配列の範囲外書き込み等を検知できる可能性がある。

  可能性があるとは、[ここ](https://triple-four.hatenablog.com/entry/20210623/1624458051#-Wshadow--%E3%82%B7%E3%83%A3%E3%83%89%E3%82%A6%E3%82%A4%E3%83%B3%E3%82%B0%E3%82%92%E8%AD%A6%E5%91%8A)でも述べられているように、必ずではない。

- `-fsanitize=address,undefined`

  `-fsanitize=address,undefined` は `-fsanitize=address` と `-fsanitize=undefined` を同時に指定したオプションである。`address` と `undefined` の間は空白なしでコンマを入れるようにすること。
