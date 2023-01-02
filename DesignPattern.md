# 課題２：デザインパターンのまとめ


## *Observerパターン*
### ObserverクラスにSubjectクラスの変更の通知するパターン。
* 説明

* 概略図

```mermaid
classDiagram
    class Subject{
        <<interface>>
        observers
        addObserver()*
        deleteObserver()*
        notifyObservers()*
        updateStatus()*
    }
    class ConcreteSubject{
        addObserver()
        deleteObserver()
        notifyObservers()
        updateStatus()
    }
    class Observer{
        <<interface>>
        update()*
    }
    class ConcreteObserverA{
        update()
    }
    class ConcreteObserverB{
        update()
    }
    Observer <|-- ConcreteObserverA : implements
    Observer <|-- ConcreteObserverB : implements
    Subject <|-- ConcreteSubject : implements
    Subject o--"*" Observer : Notifies
```

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Decoratorパターン*
### 概要
* 説明

* 概略図

```mermaid
classDiagram
    class Component{
        <<abstract>>
        method()*
    }
    class ConcreteComponent{
        method()
    }
    class Decorator{
        <<abstract>>
        component
        method()*
    }
    class ConcreteDecoratorA{
        method()
    }
    class ConcreteDecoratorB{
        method()
    }
    Decorator <|-- ConcreteDecoratorA : implements
    Decorator <|-- ConcreteDecoratorB : implements
    Component <|-- ConcreteComponent : implements
    Decorator o--|> Component
```

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Factory Methodパターン*
### 概要
* インスタンスの生成を行う専用のクラスを使う
＊複数のバリエーションを持つオブジェクトの生成をカプセル化する

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Abstract Factoryパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）

<br><br><br>
## *Singletonパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Adapterパターン*
### 概要
* 既存のインターフェースを、クライアントが望むインターフェースと互換性を持たせるために変換するパターン。継承を用いる場合と委譲を用いる場合の2種類がある。

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Facadeパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Template Methodパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Iteratorパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


<br><br><br>
## *Compositeパターン*
### 概要
* 説明

* 概略図

### 事例１
* サンプルケース

* サンプルコード

### 事例２
* サンプルケース

* サンプルコード

### その他（注意事項など，なんでも）


