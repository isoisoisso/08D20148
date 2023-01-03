# 課題1：デザインパターン個別レポート

## Mementoパターン

Mementoパターンとは、オブジェクトの状態を保存しておき、必要なときにその状態を取り出すことができるデザインパターンである。

必要な情報のみを格納するため、オブジェクトをそのまま保存するよりも容量が小さいという特徴がある。

典型的なMementoパターンは、主に3つのクラスMemento, Originator, Caretakerから構成される。Originatorが状態を保存したいオブジェクトであるとする。以下がその詳細である。

### Mementoクラス

MementoクラスはOriginatorの状態を格納するクラスであり、Originatorによって作成され、Caretakerによって保持される。

### Originatorクラス

状態を保存したいクラスである。

メソッドとして自身の状態からMementoを作成するメソッドと、Mementoを受け取りその状態になるメソッドが必要である。

### Caretakerクラス

CaretakerクラスはMementoオブジェクトを保持するクラスである。必要に応じて、複数のMementoオブジェクトを持つことがある。

Originatorの状態を保存する時はOriginatorに指示を出し、作成されたMementoをCaretakerが保持する。

Originatorの状態を戻したいときは、Caretakerが保持している任意のMementoオブジェクトをOriginatorに渡すことで、Originatorを保存しておいた状態に変更する。
