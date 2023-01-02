# 課題1：デザインパターン個別レポート

# Futureパターン

Futureパターンはマルチスレッドプログラミングのパターンの1つである．
Futureパターンでは，ある処理を別のスレッドで処理させるとき，その処理結果の取得を必要になるところまで後回しにする手法である．

この手法は処理のパイプライン化ととらえることもできる．

## インターフェース(Java)

### ExecutorService
スレッドの作成や管理を行うインターフェース．同時に実行するスレッド数を指定することができる．ただし，実行可能なスレッド数が足りない場合，実行待ちとなる．

### Callable
ExecutorServiceで実行する処理を定義するためのインターフェース．
戻り値を指定することができる．また，例外をスローすることもできる．

### Runnable
ExecutorServiceで実行する処理を定義するためのインターフェース．
Callableインターフェースと異なり戻り値を指定することが出来ない．
また，例外はRuntimeExceptionしかスロー出来ない．

## 処理手順
1. メインスレッドからExecutorServiceに別スレッドで実行するタスクを渡す．

1. ExecutorServiceがFutureを作成し，タスクと紐づけ，スレッドを起動する．

1. メインスレッドにFutureを返す．

1. ExecutorServiceによって起動されたスレッドでタスクが実行される．処理終了後にFutureに値をセットする．

1. メインスレッドはFutureに対して`get`を呼び出す．処理が終わっていた場合処理結果を受け取る．終わっていない場合，終わるまで待つ．

## 使用例
ネットワークリクエストの非同期処理などに用いる．ネットワークをバックグラウンドスレッドで処理することで，レスポンスを受信するまでのフリーズを防止することができる．

## 参考文献
https://www.ne.jp/asahi/hishidama/home/tech/java/executorservice.html

https://zenn.dev/yucatio/articles/14fe4507fde3d4

https://zawapro.com/?p=704

https://developer.android.com/guide/background/threading?hl=ja