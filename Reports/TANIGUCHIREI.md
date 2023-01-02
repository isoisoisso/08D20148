# 課題１

## Visitorパターン

振る舞いに関するパターンの一つで、オブジェクト間の相互作用に関係する。
処理をVisitorオブジェクトに記述することで処理の追加を簡単にする。
また処理対象のAccepterオブジェクトはaccpetメソッドを実装している必要がある。
Visitorパターンを佼成するクラスとして、以下のVisitor, ConcreteVisitor,Acceptor, ConcreteAcceptor,Clientがある。
## Visitorパターンを構成するクラス　

####　Visitorクラス
具体的なデータ構造の要素毎に訪問して行う処理のインターフェースを定義する。
訪問先要素の方に応じた処理はvisitメソッドを用いて指定する。
#### ConcreteVisitorクラス
Visitorで定義した各visitメソッドを実装する。
Visitorクラスのサブクラスである。
#### Acceptorクラス
Visitorの訪問先であるデータ構造要素に、accptメソッドのインターフェースを実装する。
#### ConcreteAccepterクラス
Acceptorで定義したインターフェースを実装する。
Acceptorクラスのサブクラスである。
