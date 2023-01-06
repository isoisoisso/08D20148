# Mementoパターン
あるオブジェクトの任意の時点の状態を記憶し，後でその状態にオブジェクトを戻すための工夫を提供するパターン．つまり，アンドゥを提供するパターン．

このパターンでは，状態を元に戻すための必要最小限の情報のみを保存する．

## 構成
### Originatorクラス
自分の状態をMementoとして保持したり，与えられたMementoから自身の状態を復元するクラス．

### Mementoクラス
Originatorの内部情報を保持するクラス．

### Caretakerクラス
Mementoを保持するクラス．Mementoを保持するタイミング，アンドゥするタイミングも保持する．

### クラス図
```mermaid

classDiagram
  class Originator{
    - state
    + createMemento() : Memento //Mementoオブジェクトを生成し返す
    + RestoreMemento(Memento) : void //引数のMementoのstateにレストア
  }

  class Memento{
    - state
    + GetState()
    + SetState()
  }
  class CareTaker{
    - mementoList : Memento
  }
Originator --> Memento : creates
CareTaker o--> Memento
CareTaker --> Originator : request
```
## 動作
### 状態の保存
1. CareTakerからOriginatorに`createMemento()`を実行するようリクエストする．
1. OriginatorはMementoを作成し，そのMementoの`SetState()`を実行してMementoに状態を保存する．
1. OriginatorはCareTakerに作成したMementoを返す．これをCareTakerの`mementoList`に格納する．

### 状態の復元
1. CareTakerからOriginatorに`RestoreMemento(Memento)`を実行するようリクエストする．
1. Originatorは現在の状態から`RestoreMemento(Memento)`の引数に指定されたMementoの状態へ復元する．
Mementoの情報は`GetState()`を通して取得する．

### シーケンス図
```mermaid
sequenceDiagram
  activate CareTaker
  CareTaker ->> Originator: createMemento()
  activate Originator
  Note left of CareTaker:Save state
  Originator ->> Memento: new
  Originator ->> Memento: setState()
  activate Memento
  deactivate Memento
  Originator -->> CareTaker: return memento
  deactivate Originator
  activate Originator
  CareTaker ->>+ Originator: RestoreMemento(Memento)
  Note left of CareTaker:Restore state
  Originator ->> Memento: GetState()
  activate Memento
  deactivate Memento
  deactivate Originator
```

## 長所及び短所
### 長所
- 内部の実装や状態が不明でも，オブジェクトの状態のスナップショットを作成できる．
- CareTakerに状態の保持や復元操作を分離することで，Originatorのコードを簡素化できる．

### 短所
- Mementoの大量発生により，大量のメモリが必要となる．
- 不要なMementoの廃棄する場合，CareTakerはOriginatorのライフサイクルを把握する必要がある．
